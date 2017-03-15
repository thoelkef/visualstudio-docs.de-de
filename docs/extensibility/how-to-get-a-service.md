---
title: "Gewusst wie: Abrufen eines Diensts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dienste nutzen"
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Gewusst wie: Abrufen eines Diensts
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Häufig müssen Sie Visual Studio\-Dienste auf andere Funktionen zugreifen können. Im Allgemeinen bietet Visual Studio\-Dienst eine oder mehrere Schnittstellen, die Sie verwenden können. Sie können die meisten Dienste aus einem VSPackage abrufen.  
  
 Jedem VSPackage, die von abgeleitet <xref:Microsoft.VisualStudio.Shell.Package> und, richtig positioniert alle globalen Dienst anfordern können. Da die Paketklasse implementiert <xref:System.IServiceProvider>, alle VSPackage, das Paket abgeleitet ist auch ein Dienstanbieter.  
  
 Wenn Visual Studio lädt eine <xref:Microsoft.VisualStudio.Shell.Package>, übergibt ein <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> \-Objekt an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode während der Initialisierung. Dies wird als *Positionierung* VSPackage. Die Paket\-Klasse umschließt diese Dienstanbieter und stellt die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode zum Abrufen von Diensten.  
  
## Abrufen eines Diensts aus einer initialisierten VSPackage  
  
1.  Alle Visual Studio\-Erweiterung beginnt mit der ein VSIX\-Bereitstellungsprojekt, das die Ressourcen für die Erweiterung enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX\-Projekt namens `GetServiceExtension`. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Jetzt fügen Sie eine benutzerdefinierten Befehl Elementvorlage mit dem Namen **GetServiceCommand**. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **Befehl benutzerdefinierte**. In den **Namen** Feld am unteren Rand des Fensters, das Ändern der Name der Befehlsdatei an **GetServiceCommand.cs**. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  Entfernen Sie in GetServiceCommand.cs den Text der MenuItemCommand\-Methode, und fügen Sie den folgenden Code hinzu:  
  
    ```c#  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (activityLog == null) return; System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Dieser Code Ruft eine SVsActivityLog\-Dienst ab und wandelt es auf eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> \-Schnittstelle, die zum Schreiben in die Protokolldatei für die Aktivität verwendet werden kann. Ein Beispiel finden Sie unter [Gewusst wie: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
5.  Suchen Sie im Menü Extras der experimentellen Instanz den **aufrufen GetServiceCommand** Schaltfläche. Wenn Sie auf diese Schaltfläche klicken, sollte ein Meldungsfeld mit der Meldung **den Protokolldienst Aktivität gefunden.**  
  
## Abrufen von einem Dienst aus einem Werkzeugcontainer Fensters oder Steuerelements  
 Manchmal müssen Sie Abrufen eines Diensts aus einem Toolfenster oder Steuern von Container, der hat nicht platziert wurde, andernfalls hat bei einem Dienstanbieter, der nicht über den Dienst kennt gewünschte platziert wurde. Sie möchten z. B. im Aktivitätsprotokoll von in einem Steuerelement zu schreiben.  
  
 Die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> \-Methode beruht auf einem zwischengespeicherten Dienstanbieter, die zum ersten Mal initialisiert wird jedem VSPackage abgeleitet <xref:Microsoft.VisualStudio.Shell.Package> platziert.  
  
 Da der VSPackage\-Konstruktor aufgerufen wird, bevor das VSPackage platziert wird, sind globale Dienste in der Regel nicht von innerhalb des Konstruktors VSPackage verfügbar. Finden Sie unter [Gewusst wie: Problembehandlung bei Services](../extensibility/how-to-troubleshoot-services.md) für das Problem zu umgehen.  
  
 Hier ist ein Beispiel für die Möglichkeit, einen Dienst in einem Toolfenster oder andere nicht VSPackage\-Element zu erhalten.  
  
```c#  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
## Abrufen eines Diensts vom DTE\-Objekt  
 Sie erhalten auch Dienste von <xref:EnvDTE.DTEClass> Objekt. Allerdings benötigen Sie das DTE\-Objekt als Dienst aus einem VSPackage oder durch Aufrufen der statischen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode.  
  
 Das DTE\-Objekt implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, die Sie verwenden können, Abfragen eines Diensts mit <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Gewusst wie: Abrufen ein Diensts vom DTE\-Objekt ist  
  
```c#  
// Start with the DTE object, for example: // using EnvDTE; // DTE dte = (DTE)GetService(typeof(DTE)); ServiceProvider sp = new ServiceProvider((Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte); if (sp != null) { IVsActivityLog log = sp.GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log != null) { System.Windows.Forms.MessageBox.Show("Found the activity log service."); } }  
```  
  
## Siehe auch  
 [Gewusst wie: Bereitstellen ein Diensts](../extensibility/how-to-provide-a-service.md)   
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)