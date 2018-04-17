---
title: 'Vorgehensweise: Problembehandlung bei Services | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9efe3c1c7032f1db41272a03cf689e015a79522
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-troubleshoot-services"></a>Vorgehensweise: Services-Problembehandlung
Es gibt einige allgemeine Probleme, die auftreten können, wenn Sie versuchen, einen Dienst zu erhalten:  
  
-   Der Dienst ist nicht registriert, mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Der Dienst wird vom Schnittstellentyp und nicht vom Diensttyp angefordert.  
  
-   Das VSPackage, das den Dienst anfordern ist nicht positioniert wurde.  
  
-   Der falsche Service-Anbieter wird verwendet.  
  
 Wenn der angeforderte Dienst kann nicht abgerufen werden, wird den Aufruf von <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> gibt null zurück. Sie sollten immer auf Null testen, nach dem Anfordern eines Diensts:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Problembehandlung für einen Dienst  
  
1.  Überprüfen Sie die systemregistrierung, um festzustellen, ob der Dienst ordnungsgemäß registriert wurde. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen ein Diensts](../extensibility/how-to-provide-a-service.md).  
  
     Das folgende Fragment einer REG-Datei zeigt, wie der SVsTextManager-Dienst registriert werden kann:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     Im obigen Beispiel ist die Versionsnummer die Version des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], wie z. B. 12.0 oder 14.0, der Schlüssel {F5E7E71D-1401-11d1-883B-0000F87579D2} ist die Dienst-ID (SID) des Diensts, SVsTextManager und der standardmäßige Wert { F5E7E720-1401-11D1-883B-0000F87579D2} ist die Paket-GUID des TextManager-VSPackage, das den Dienst bereitstellt.  
  
2.  Verwenden Sie den Diensttyp und nicht den Schnittstellentyp, wenn Sie GetService sicher aufgerufen. Beim Anfordern eines Diensts aus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> extrahiert die GUID des Typs. Ein Dienst wird nicht gefunden werden, wenn folgende Bedingungen zutreffen:  
  
    1.  Ein Schnittstellentyp an GetService anstelle der Diensttyp übergeben wird.  
  
    2.  Die Schnittstelle ist explizit keine GUID zugewiesen. Daher erstellt das System einen Standard-GUID für ein Objekt nach Bedarf.  
  
3.  Achten Sie darauf, dass das VSPackage, das den Dienst anfordern positioniert wurde. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eine VSPackage Sites, nach dem Erstellen es und vor dem Aufruf <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Wenn Sie Code in einem VSPackage-Konstruktor verfügen, die ein Dienst benötigt, auf die Initialize-Methode verschieben.  
  
4.  Achten Sie darauf, dass Sie den richtigen Service-Anbieter verwenden.  
  
     Nicht alle Dienstanbieter sind bis auf eine. Der Dienstanbieter, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Durchläufe auszuführen, um ein Toolfenster unterscheidet sich von der für einer VSPackage übergibt. Das Tool-Fenster-Dienstanbieter kennt <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, aber nicht kennt <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Sie können Aufrufen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> zum Abrufen eines Dienstanbieters VSPackage innerhalb eines Toolfensters.  
  
     Wenn ein Toolfenster ein Benutzersteuerelement oder einem anderen Steuerelementcontainer hostet, wird der Container wird durch die Windows-Komponentenmodell platziert werden und keinen Zugriff auf alle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Dienste. Sie können Aufrufen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> einen Dienstanbieter für VSPackage in einem Steuerelementcontainers abgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Liste der verfügbaren Dienste](../extensibility/internals/list-of-available-services.md)   
 [Verwenden und die Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)