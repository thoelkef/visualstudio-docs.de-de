---
title: 'Vorgehensweise: Abrufen eines Diensts | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46ef86b8cde506aad3e00aa6b5dbc6470c0087de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204185"
---
# <a name="how-to-get-a-service"></a>Vorgehensweise: Abrufen eines Diensts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Häufig müssen Sie Visual Studio-Diensten Zugriff auf verschiedene Features zu erhalten. Im Allgemeinen bietet Visual Studio-Dienst eine oder mehrere Schnittstellen, die Sie verwenden können. Sie können die meisten Dienste aus einem VSPackage abrufen.  
  
 Alle VSPackage, das von abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Package> , richtig positioniert, und lassen sich für einen globalen Dienst. Da die Paketklasse implementiert <xref:System.IServiceProvider>, jedem VSPackage, die vom Paket abgeleitet wird, ist auch ein Dienstanbieter.  
  
 Beim Laden von Visual Studio eine <xref:Microsoft.VisualStudio.Shell.Package>, übergibt ein <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> -Objekt an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode während der Initialisierung. Dies wird als bezeichnet *Positionierung* das VSPackage. Die Paket-Klasse dient als Wrapper für diese Dienstanbieter bereit und ermöglicht die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode zum Abrufen von Diensten.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Abrufen eines Diensts aus einer initialisierten VSPackage  
  
1. Alle Visual Studio-Erweiterung beginnt mit dem ein VSIX-Bereitstellung-Projekt, das die Ressourcen für die Erweiterung enthält. Erstellen Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX-Projekt namens `GetServiceExtension`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2. Fügen Sie jetzt eine benutzerdefinierten Befehl-Elementvorlage, die mit dem Namen **GetServiceCommand**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Befehls**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **GetServiceCommand.cs**. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3. Klicken Sie im GetServiceCommand.cs entfernen Sie den Text der MenuItemCommand-Methode, und fügen Sie den folgenden Code:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Dieser Code Ruft eine SVsActivityLog-Dienst ab und wandelt es diesen auf eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> -Schnittstelle, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).  
  
4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
5. Suchen Sie im Menü Extras der experimentellen Instanz den **aufrufen GetServiceCommand** Schaltfläche. Wenn Sie diese Schaltfläche klicken, sollten Sie sehen, dass ein Dialogfeld mit der Meldung **der Ereignisprotokolldienst Aktivität gefunden.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Abrufen eines Diensts aus einem Werkzeugcontainer Fensters oder Steuerelements  
 Manchmal müssen Sie zum Abrufen eines Diensts aus einem Toolfenster oder steuern, Container, der ist nicht positioniert wurde, andernfalls ist bei einem Dienstanbieter, der nicht über den Dienst kennt gewünschten positioniert wurde. Beispielsweise empfiehlt es sich zum Schreiben in das Aktivitätsprotokoll in einem Steuerelement aus.  
  
 Die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode beruht auf einer zwischengespeicherten Dienstanbieter, der zum ersten Mal initialisiert wird jedem VSPackage abgeleitet <xref:Microsoft.VisualStudio.Shell.Package> positioniert ist.  
  
 Da der VSPackage-Konstruktor aufgerufen wird, bevor das VSPackage platziert wird, sind globale Dienste in der Regel nicht von innerhalb des VSPackage-Konstruktors verfügbar. Weitere Informationen finden Sie unter [How to: Problembehandlung bei Services](../extensibility/how-to-troubleshoot-services.md) für dieses Problem zu umgehen.  
  
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
 [Vorgehensweise: Geben Sie einen Dienst](../extensibility/how-to-provide-a-service.md)   
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)
