---
title: 'Vorgehensweise: Problembehandlung bei Diensten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5311aa3ff390611942aa91cb1f2a53ca5a76258d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204068"
---
# <a name="how-to-troubleshoot-services"></a>Gewusst wie: Problembehandlung bei Diensten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es gibt mehrere häufige Probleme, die auftreten können, wenn Sie versuchen, einen Dienst zu erhalten:  
  
- Der Dienst ist nicht bei registriert [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Der Dienst wird vom Schnittstellentyp und nicht vom Diensttyp angefordert.  
  
- Das VSPackage, das den Dienst anfordert, wurde nicht positioniert.  
  
- Es wird der falsche Dienstanbieter verwendet.  
  
  Wenn der angeforderte Dienst nicht abgerufen werden kann, gibt der-Rückruf den Wert <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> NULL zurück. Nach dem Anfordern eines Dienstanbieter sollten Sie immer auf NULL testen:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>So beheben Sie Probleme mit einem Dienst  
  
1. Überprüfen Sie die Systemregistrierung, um festzustellen, ob der Dienst ordnungsgemäß registriert wurde. Weitere Informationen finden Sie unter [Registrieren von Diensten](../misc/registering-services.md).  
  
     Das folgende. reg-Datei Fragment zeigt, wie der SVsTextManager-Dienst registriert werden kann:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     Im obigen Beispiel ist die Versionsnummer die Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , wie z. b. 12,0 oder 14,0, der Schlüssel {F5E7E71D-1401-11d1-883B-0000F87579D2} ist die Dienst-ID (SID) des Diensts (SVsTextManager), und der Standardwert {F5E7E720-1401-11d1-883B-0000F87579D2} ist die Paket-GUID des Text Manager-VSPackage, das den Dienst bereitstellt.  
  
2. Verwenden Sie den Diensttyp und nicht den Schnittstellentyp, wenn Sie GetService aufrufen. Wenn Sie einen Dienst von anfordern [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , <xref:Microsoft.VisualStudio.Shell.Package> extrahiert die GUID aus dem-Typ. Ein Dienst wird nicht gefunden, wenn die folgenden Bedingungen erfüllt sind:  
  
    1. Ein Schnittstellentyp wird an GetService statt an den Diensttyp übermittelt.  
  
    2. Der-Schnittstelle ist keine GUID explizit zugewiesen. Daher erstellt das System bei Bedarf eine Standard-GUID für ein Objekt.  
  
3. Stellen Sie sicher, dass das VSPackage, das den Dienst anfordert, positioniert wurde. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Websites ein VSPackage nach dem Erstellen und vor dem Aufrufen von <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
     Wenn Sie über Code in einem VSPackage-Konstruktor verfügen, der einen Dienst benötigt, verschieben Sie ihn in die Initialize-Methode.  
  
4. Stellen Sie sicher, dass Sie den richtigen Dienstanbieter verwenden.  
  
     Nicht alle Dienstanbieter sind gleich. Der Dienstanbieter, der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] an ein Tool Fenster übergibt, unterscheidet sich von dem, der an ein VSPackage weitergeleitet wird. Der Tool Fenster-Dienstanbieter kennt <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> sich, weiß aber nicht <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Sie können abrufen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> , um einen VSPackage-Dienstanbieter innerhalb eines Tool Fensters abzurufen.  
  
     Wenn ein Tool Fenster ein Benutzer Steuerelement oder einen anderen Steuerelement Container hostet, wird der Container vom Windows-Komponentenmodell positioniert und hat keinen Zugriff auf [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Dienste. Sie können abrufen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> , um einen VSPackage-Dienstanbieter innerhalb eines Steuerelement Containers abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Liste der verfügbaren Dienste](../extensibility/internals/list-of-available-services.md)   
 [Verwenden von und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)
