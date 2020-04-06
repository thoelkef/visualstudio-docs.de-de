---
title: 'Gewusst wie: Erhalten Sie einen Service | Microsoft Docs'
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- services, consuming
ms.assetid: 1f000020-8fb7-4e39-8e1e-2e38c7fec3d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8e6f20eaa08d6bb7aaa0cc9e560856daa5959e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710958"
---
# <a name="how-to-get-a-service"></a>Gewusst wie: Holen Sie sich einen Service

Häufig müssen Sie Visual Studio-Dienste abrufen, um auf verschiedene Funktionen zugreifen zu können. Im Allgemeinen stellt ein Visual Studio-Dienst eine oder mehrere Schnittstellen bereit, die Sie verwenden können. Sie können die meisten Dienste von einem VSPackage abrufen.

Jedes VSPackage, das <xref:Microsoft.VisualStudio.Shell.Package> von einem beliebigen und korrekt eingerichteten VsPackage abstammt, kann nach jedem globalen Dienst fragen. Da `Package` die Klasse <xref:System.IServiceProvider>implementiert, ist jedes VSPackage, das von `Package` einem Dienstanbieter stammt, ebenfalls ein Dienstanbieter.

Wenn Visual Studio <xref:Microsoft.VisualStudio.Shell.Package>eine lädt, wird während der Initialisierung ein <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Objekt an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode weitergereicht. Dies wird als *Sitzen* des VSPackage bezeichnet. Die `Package` Klasse umschließt diesen Dienstanbieter <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> und stellt die Methode zum Abrufen von Diensten bereit.

## <a name="getting-a-service-from-an-initialized-vspackage"></a>Abrufen eines Dienstes aus einem initialisierten VSPackage

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungsprojekt, das die Erweiterungselemente enthält. Erstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sie ein `GetServiceExtension`VSIX-Projekt mit dem Namen . Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Fügen Sie nun eine benutzerdefinierte Befehlselementvorlage mit dem Namen **GetServiceCommand**hinzu. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C-Extensibility,** > **Extensibility** und wählen Sie **Benutzerdefinierter Befehl aus.** Ändern Sie im Feld **Name** am unteren Rand des Fensters den Befehlsdateinamen in *GetServiceCommand.cs*. Weitere Informationen zum Erstellen eines benutzerdefinierten Befehls finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md)

3. Entfernen *Sie in GetServiceCommand.cs* `MenuItemCommand` den Text der Methode, und fügen Sie den folgenden Code hinzu:

   ```csharp
   IVsActivityLog activityLog = ServiceProvider.GetService(typeof(SVsActivityLog)) as IVsActivityLog;
   if (activityLog == null) return;
   System.Windows.Forms.MessageBox.Show("Found the activity log service.");

   ```

    Dieser Code ruft einen SVsActivityLog-Dienst <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> ab und gibt ihn in eine Schnittstelle um, die zum Schreiben in das Aktivitätsprotokoll verwendet werden kann. Ein Beispiel finden Sie unter [Gewusst wie: Verwenden des Aktivitätsprotokolls](../extensibility/how-to-use-the-activity-log.md).

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

5. Suchen Sie im Menü **Extras** der experimentellen Instanz nach der Schaltfläche **GetServiceCommand aufrufen.** Wenn Sie auf diese Schaltfläche klicken, sollte ein Meldungsfeld mit der Meldung **"Den Aktivitätsprotokolldienst gefunden"** angezeigt werden.

## <a name="getting-a-service-from-a-tool-window-or-control-container"></a>Abrufen eines Dienstes aus einem Toolfenster oder Steuercontainer

Manchmal müssen Sie einen Dienst aus einem Toolfenster oder Einem Steuerelementcontainer abrufen, der nicht standortgebunden ist, oder sie wurden bei einem Dienstanbieter eingerichtet, der den gewünschten Dienst nicht kennt. Sie können z. B. innerhalb eines Steuerelements in das Aktivitätsprotokoll schreiben.

Die <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> statische Methode basiert auf einem zwischengespeicherten Dienstanbieter, der initialisiert wird, wenn ein von <xref:Microsoft.VisualStudio.Shell.Package> VSPackage abgeleitetes VSPackage zum ersten Mal lokalisiert wird.

Da der VSPackage-Konstruktor aufgerufen wird, bevor das VSPackage standortbasiert ist, sind globale Dienste in der Regel nicht innerhalb des VSPackage-Konstruktors verfügbar. Weitere Informationen finden Sie [unter Gewusst wie: Beheben von Diensten](../extensibility/how-to-troubleshoot-services.md) für eine Problemumgehung.

Hier ist ein Beispiel für die Art und Weise, wie Sie einen Dienst in einem Toolfenster oder einem anderen Nicht-VSPackage-Element abrufen.

```csharp
IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="getting-a-service-from-the-dte-object"></a>Abrufen eines Dienstes aus dem DTE-Objekt

Sie können auch <xref:EnvDTE.DTEClass> Dienste vom Objekt abrufen. Sie müssen das DTE-Objekt jedoch als Dienst von einem <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> VSPackage abrufen oder die statische Methode aufrufen.

Das DTE-Objekt <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>implementiert , mit dem Sie einen <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>Dienst mithilfe von abfragen können.

Hier erfahren Sie, wie Sie einen Dienst aus dem DTE-Objekt abrufen.

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

## <a name="see-also"></a>Weitere Informationen

- [Gewusst wie: Bereitstellen eines Dienstes](../extensibility/how-to-provide-a-service.md)
- [Nutzung und Bereitstellung von Dienstleistungen](../extensibility/using-and-providing-services.md)
- [Service-Essentials](../extensibility/internals/service-essentials.md)
