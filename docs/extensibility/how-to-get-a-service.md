---
title: 'Vorgehensweise: Abrufen eines Diensts | Microsoft Docs'
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
ms.openlocfilehash: cdf5bd925a034a64d8605c675704a0e894308ea3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-get-a-service"></a>Vorgehensweise: Abrufen eines Diensts
Häufig müssen Sie Visual Studio-Diensten den Zugriff auf andere Funktionen zu erhalten. Im Allgemeinen bietet ein Visual Studio-Dienst eine oder mehrere Schnittstellen, die Sie verwenden können. Sie können die meisten Dienste aus einem VSPackage abrufen.  
  
 Alle VSPackage, das von abgeleitet ist <xref:Microsoft.VisualStudio.Shell.Package> und, ordnungsgemäß positioniert können Fragen für globale Dienste. Da die Paketklasse implementiert <xref:System.IServiceProvider>, alle VSPackage, das Paket abgeleitet ist auch ein Dienstanbieter.  
  
 Visual Studio beim Laden einer <xref:Microsoft.VisualStudio.Shell.Package>, übergibt ein <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> -Objekt an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode während der Initialisierung. Hierbei spricht *Positionierung* das VSPackage. Die Paket-Klasse dient als Wrapper für diese Dienstanbieter bereit und ermöglicht die <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> Methode zum Abrufen von Diensten.  
  
## <a name="getting-a-service-from-an-initialized-vspackage"></a>Abrufen eines Diensts aus einer initialisierten VSPackage  
  
1.  Alle Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellung-Projekt bzw. die die Erweiterung Ressourcen enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `GetServiceExtension`. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# > Erweiterbarkeit**.  
  
2.  Fügen Sie jetzt eine Elementvorlage für benutzerdefinierte Befehl mit dem Namen **GetServiceCommand**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# > Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Befehl**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **GetServiceCommand.cs**. Weitere Informationen zur Vorgehensweise beim Erstellen eines benutzerdefinierten Befehls [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
3.  Entfernen Sie den Text der Methode MenuItemCommand GetServiceCommand.cs ein, und fügen Sie den folgenden Code hinzu:  
  
    ```csharp  
    IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    if (activityLog == null) return;  
    System.Windows.Forms.MessageBox.Show("Found the activity log service.");  
  
    ```  
  
     Dieser Code Ruft eine SVsActivityLog-Dienst ab und wandelt es zu einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> Schnittstelle, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter [Vorgehensweise: Verwenden Sie das Aktivitätsprotokoll](../extensibility/how-to-use-the-activity-log.md).  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
5.  Suchen Sie im Menü Extras der experimentellen Instanz den **GetServiceCommand Aufrufen** Schaltfläche. Wenn Sie auf diese Schaltfläche klicken, sehen Sie ein Dialogfeld mit der Meldung **Protokolldienst Aktivität gefunden.**  
  
## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Abrufen eines Diensts aus einem Tool Fenster- oder Steuerelement-container  
 In einigen Fällen müssen Sie möglicherweise zum Abrufen eines Diensts aus einem Toolfenster oder Steuern von Container, der wurde nicht platziert wurde, sonst hat mit einem Service-Anbieter, der nicht über den Dienst kennt gewünschten positioniert wurde. Sie möchten z. B. in das Aktivitätsprotokoll aus in einem Steuerelement zu schreiben.  
  
 Die statische <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode beruht auf einer zwischengespeicherten Dienstanbieter, der zum ersten Mal initialisiert wird VSPackage abgeleitet <xref:Microsoft.VisualStudio.Shell.Package> positioniert ist.  
  
 Da der VSPackage-Konstruktor aufgerufen wird, bevor das VSPackage positioniert wird, werden globale Dienste in der Regel nicht verfügbar, in der VSPackage-Konstruktor. Finden Sie unter [wie: Problembehandlung Services](../extensibility/how-to-troubleshoot-services.md) für dieses Problem zu umgehen.  
  
 Hier ist ein Beispiel für die Möglichkeit, einen Dienst in einem Toolfenster oder andere nicht VSPackage-Element zu erhalten.  
  
```csharp  
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="getting-a-service-from-the-dte-object"></a>Abrufen eines Diensts vom DTE-Objekt  
 Sie können auch Dienste von abrufen <xref:EnvDTE.DTEClass> Objekt. Allerdings benötigen Sie das DTE-Objekt als Dienst aus einem VSPackage oder durch Aufrufen der statischen <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> Methode.  
  
 Das DTE-Objekt implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>, die Sie verwenden können zum Abfragen eines Diensts mit <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>.  
  
 Im folgenden wird zum Abrufen eines Diensts vom DTE-Objekt.  
  
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
 [Vorgehensweise: Bereitstellen ein Diensts](../extensibility/how-to-provide-a-service.md)   
 [Verwenden und die Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)