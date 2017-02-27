---
title: "Gewusst wie: Problembehandlung bei Services | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Problembehandlung bei Services"
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Gewusst wie: Problembehandlung bei Services
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Es gibt verschiedene Probleme, die auftreten können, wenn Sie versuchen, einen Dienst zu erhalten:  
  
-   Der Dienst ist nicht registriert, mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Der Dienst wird durch den Schnittstellentyp und nicht vom Typ angefordert.  
  
-   Das Anfordern des Dienstes VSPackage ist nicht positioniert wurde.  
  
-   Der falsche Dienstanbieter ist verwendet.  
  
 Wenn der angeforderte Dienst kann nicht abgerufen werden, wird den Aufruf von <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> gibt null zurück. Sie sollten immer auf Null testen, nach dem Anfordern eines Diensts:  
  
```c#  
IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
### Problembehandlung für einen Dienst  
  
1.  Überprüfen Sie die systemregistrierung, um festzustellen, ob der Dienst ordnungsgemäß registriert wurde. Weitere Informationen finden Sie unter [Registrieren von Diensten](../misc/registering-services.md).  
  
     Das folgende Fragment einer REG\-Datei zeigt, wie der SVsTextManager\-Dienst registriert werden kann:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
    ```  
  
     Im obigen Beispiel ist die Versionsnummer die Version [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], z. B. 12.0 oder 14.0, der Schlüssel {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} die Dienst\-ID \(SID\) des Diensts, SVsTextManager, und der Standardwert {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} ist die Paket\-GUID des Text\-Managers VSPackage, das den Dienst bereitstellt.  
  
2.  Verwenden Sie den Diensttyp und nicht den Typ der beim Aufrufen der GetService. Beim Anfordern eines Diensts aus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrahiert die GUID vom Typ. Ein Dienst wird nicht gefunden werden, wenn folgende Punkte:  
  
    1.  Ein Schnittstellentyp ist an GetService anstelle der Diensttyp übergeben.  
  
    2.  Keine GUID der Schnittstelle explizit zugewiesen. Daher erstellt das System einen Standard\-GUID für ein Objekt nach Bedarf.  
  
3.  Achten Sie darauf, dass das Anfordern des Dienstes VSPackage positioniert wurde.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ein VSPackage Sites, nachdem es erstellen und vor dem Aufruf von <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Wenn Sie Code in einem VSPackage\-Konstruktor verfügen, mit denen einen Dienst, verschieben Sie sie in der Initialize\-Methode.  
  
4.  Achten Sie darauf, dass Sie den richtigen Service\-Anbieter verwenden.  
  
     Nicht alle Dienstanbieter sind gleich. Der Dienstanbieter, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] übergibt, ein Toolfenster unterscheidet sich von der zu einem VSPackage übergibt. Die Tool\-Fenster\-Dienstanbieter kennt <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, aber nicht kennt <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> um ein VSPackage\-Dienstanbieter, von innerhalb eines Toolfensters zu erhalten.  
  
     Wenn ein Toolfenster ein Benutzersteuerelement oder einem anderen Steuerelementcontainer hostet, wird der Container wird durch das Windows\-Komponentenmodell platziert werden und haben keinen Zugriff auf alle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Dienste. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> um ein VSPackage\-Dienstanbieter aus in einem Steuerelementcontainers abzurufen.  
  
## Siehe auch  
 [Liste der verfügbaren Dienste](../extensibility/internals/list-of-available-services.md)   
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)