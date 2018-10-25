---
title: 'Vorgehensweise: Abrufen eines Diensts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b7b28f018ba92ad2ab8a266311ac2e71fd910440
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951378"
---
# <a name="how-to-get-a-service"></a>Gewusst wie: Abrufen eines Diensts
Häufig müssen Sie Visual Studio-Diensten Zugriff auf verschiedene Features zu erhalten. Im Allgemeinen bietet Visual Studio-Dienst eine oder mehrere Schnittstellen, die Sie verwenden können. Sie können die meisten Dienste aus einem VSPackage abrufen.  
  
 Alle VSPackage, das von abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Package> , richtig positioniert, und lassen sich für einen globalen Dienst. Da die `Package` -Klasse implementiert <xref:System.IServiceProvider>, alle VSPackage, das von abgeleitet ist `Package` ist auch ein Dienstanbieter.  
  
 Beim Laden von Visual Studio eine <xref:Microsoft.VisualStudio.Shell.Package>, übergibt ein <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> -Objekt an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode während der Initialisierung. Dies wird als bezeichnet *Positionierung* das VSPackage. Die `Package` Klasse dient als Wrapper für diese Dienstanbieter bereit und ermöglicht die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode zum Abrufen von Diensten.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Abrufen eines Diensts aus einer initialisierten VSPackage  
  
1. Alle Visual Studio-Erweiterung beginnt mit dem ein VSIX-Bereitstellung-Projekt, das die Ressourcen für die Erweiterung enthält. Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `GetServiceExtension`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual C#-** > **Erweiterbarkeit**.  
  
2. Fügen Sie jetzt eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **GetServiceCommand**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C#-** > **Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an *GetServiceCommand.cs*. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3. In *GetServiceCommand.cs*, entfernen Sie den Text, der die `MenuItemCommand` Methode, und fügen Sie den folgenden Code hinzu:  
  
   ```csharp  
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
   if (activityLog == null) return;  
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
   ```  
  
    Dieser Code Ruft eine SVsActivityLog-Dienst ab und wandelt es diesen auf eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> -Schnittstelle, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter [Vorgehensweise: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).  
  
4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
5. Auf der **Tools** finden Sie im Menü der experimentellen Instanz den **aufrufen GetServiceCommand** Schaltfläche. Wenn Sie diese Schaltfläche klicken, sollten Sie sehen, dass ein Dialogfeld mit der Meldung **der Ereignisprotokolldienst Aktivität gefunden.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Abrufen eines Diensts aus einem Werkzeugcontainer Fensters oder Steuerelements  
 Manchmal müssen Sie zum Abrufen eines Diensts aus einem Toolfenster oder steuern, Container, der ist nicht positioniert wurde, andernfalls ist bei einem Dienstanbieter, der nicht über den Dienst kennt gewünschten positioniert wurde. Beispielsweise empfiehlt es sich zum Schreiben in das Aktivitätsprotokoll in einem Steuerelement aus.  
  
 Die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode beruht auf einer zwischengespeicherten Dienstanbieter, der zum ersten Mal initialisiert wird jedem VSPackage abgeleitet <xref:Microsoft.VisualStudio.Shell.Package> positioniert ist.  
  
 Da der VSPackage-Konstruktor aufgerufen wird, bevor das VSPackage platziert wird, sind globale Dienste in der Regel nicht von innerhalb des VSPackage-Konstruktors verfügbar. Finden Sie unter [wie: Problembehandlung bei Services](../extensibility/how-to-troubleshoot-services.md) für dieses Problem zu umgehen.  
  
 Hier ist ein Beispiel für die Möglichkeit, einen Dienst in einem Toolfenster oder andere nicht-VSPackage-Element abzurufen.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Abrufen eines Diensts vom DTE-Objekt  
 Sie können auch Dienste abrufen <xref:EnvDTE.DTEClass> Objekt. Allerdings muss man das DTE-Objekt als Dienst aus einem VSPackage oder durch Aufrufen der statischen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode.  
  
 Das DTE-Objekt implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, die Sie verwenden können, Abfragen eines Diensts mithilfe von <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Hier ist zum Abrufen eines Diensts vom DTE-Objekt.  
  
```csharp  
// Start with the DTE object, for example:   
// using EnvDTE;  
// DTE dte = (DTE)GetService(typeof(DTE));  
  
ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
if (sp != null)  
{  
    IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (log != null)  
    {   
        System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
    }  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Bereitstellen ein Diensts](../extensibility/how-to-provide-a-service.md)   
 [Verwenden und Dienste bereitstellen](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)