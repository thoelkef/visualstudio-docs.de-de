---
title: Bereitstellung von Befehlen | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707333"
---
# <a name="making-commands-available"></a>Bereitstellung von Befehlen

Wenn Visual Studio mehrere VSPackages hinzugefügt werden, kann die Benutzeroberfläche (UI) mit Befehlen überfüllt sein. Sie können Ihr Paket wie folgt programmieren, um dieses Problem zu reduzieren:

- Programmieren Sie das Paket so, dass es nur geladen wird, wenn ein Benutzer es benötigt.

- Programmieren Sie das Paket so, dass seine Befehle nur angezeigt werden, wenn sie im Kontext des aktuellen Status der integrierten Entwicklungsumgebung (IDE) erforderlich sein können.

## <a name="delayed-loading"></a>Verzögerte Beladung

Die typische Möglichkeit, das verzögerte Laden zu aktivieren, besteht darin, das VSPackage so zu entwerfen, dass seine Befehle in der Benutzeroberfläche angezeigt werden, das Paket selbst jedoch erst geladen wird, wenn ein Benutzer auf einen der Befehle klickt. Um dies zu erreichen, erstellen Sie in der .vsct-Datei Befehle, die keine Befehlsflags haben.

Das folgende Beispiel zeigt die Definition eines Menübefehls aus einer .vsct-Datei. Dies ist der Befehl, der von der Visual Studio-Paketvorlage generiert wird, wenn die **Menübefehlsoption** in der Vorlage ausgewählt ist.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

Wenn im Beispiel die übergeordnete `MyMenuGroup`Gruppe , ein untergeordnetes Element eines Menüs der obersten Ebene wie dem Menü **Extras** ist, wird der Befehl in diesem Menü angezeigt, aber das Paket, das den Befehl ausführt, wird erst geladen, wenn ein Benutzer auf den Befehl geklickt hat. Durch Programmieren des Befehls <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zur Implementierung der Schnittstelle können Sie jedoch aktivieren, dass das Paket geladen wird, wenn das Menü, das den Befehl enthält, zum ersten Mal erweitert wird.

Beachten Sie, dass verzögertes Laden auch die Anlaufleistung verbessern kann.

## <a name="current-context-and-the-visibility-of-commands"></a>Aktueller Kontext und Sichtbarkeit von Befehlen

Sie können VSPackage-Befehle so programmieren, dass sie sichtbar oder ausgeblendet sind, abhängig vom aktuellen Status der VSPackage-Daten oder den aktuell relevanten Aktionen. Sie können das VSPackage aktivieren, um den Status seiner Befehle <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> festzulegen, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> in der Regel mithilfe einer Implementierung der Methode von der Schnittstelle, aber dies erfordert, dass das VSPackage geladen wird, bevor es den Code ausführen kann. Stattdessen wird empfohlen, dass Sie die IDE aktivieren, um die Sichtbarkeit der Befehle zu verwalten, ohne das Paket zu laden. Zu diesem Zweck ordnen Sie befehle in der Datei .vsct einem oder mehreren speziellen UI-Kontexten zu. Diese UI-Kontexte werden durch eine GUID identifiziert, die als *Befehlskontext-GUID*bezeichnet wird.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]überwacht Änderungen, die sich aus Benutzeraktionen ergeben, z. B. das Laden eines Projekts oder das Wechseln von der Bearbeitung zum Erstellen. Wenn Änderungen auftreten, wird das Erscheinungsbild der IDE automatisch geändert. Die folgende Tabelle zeigt vier Hauptkontexte der IDE-Änderung, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überwacht werden.

| Art des Kontexts | BESCHREIBUNG |
|-------------------------| - |
| Aktiver Projekttyp | Bei den meisten `GUID` Projekttypen entspricht dieser Wert der GUID des VSPackage, das das Projekt implementiert. [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte verwenden jedoch den `GUID` Projekttyp als Wert. |
| Aktives Fenster | In der Regel ist dies das letzte aktive Dokumentfenster, das den aktuellen UI-Kontext für Schlüsselbindungen festlegt. Es könnte sich jedoch auch um ein Toolfenster mit einer Schlüsselbindungstabelle befinden, die dem internen Webbrowser ähnelt. Für Dokumentfenster mit mehreren Registerkarten, z. B. den `GUID`HTML-Editor, hat jede Registerkarte einen anderen Befehlskontext . |
| Aktiver Sprachdienst | Der Sprachdienst, der der Datei zugeordnet ist, die derzeit in einem Texteditor angezeigt wird. |
| Aktives Werkzeugfenster | Ein Toolfenster, das geöffnet ist und den Fokus hat. |

Ein fünfter wichtiger Kontextbereich ist der UI-Status der IDE. UI-Kontexte werden durch `GUID`den aktiven Befehlskontext s wie folgt identifiziert:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Diese GUIDs werden je nach aktuellem Zustand der IDE als aktiv oder inaktiv markiert. Mehrere UI-Kontexte können gleichzeitig aktiv sein.

### <a name="hide-and-display-commands-based-on-context"></a>Ausblendung und Anzeige von Befehlen basierend auf dem Kontext

Sie können einen Paketbefehl in der IDE anzeigen oder ausblenden, ohne das Paket selbst zu laden. Definieren Sie dazu den Befehl in der .vsct-Datei `DefaultDisabled` `DefaultInvisible`des `DynamicVisibility` Pakets, indem Sie die Flags , und Befehl verwenden und ein oder mehrere [VisibilityItem-Elemente](../../extensibility/visibilityitem-element.md) zum Abschnitt [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) hinzufügen. Wenn ein angegebener Befehlskontext `GUID` aktiv wird, wird der Befehl angezeigt, ohne das Paket zu laden.

### <a name="custom-context-guids"></a>Benutzerdefinierte Kontext-GUIDs

Wenn eine entsprechende Befehlskontext-GUID noch nicht definiert ist, können Sie eine in Ihrem VSPackage definieren und diese dann so programmieren, dass sie aktiv oder inaktiv ist, um die Sichtbarkeit Ihrer Befehle zu steuern. Verwenden <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Sie den Dienst, um:

- Registrieren Sie Kontext-GUIDs <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (durch Aufrufen der Methode).

- Rufen Sie den `GUID` Status eines <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Kontexts ab (durch Aufrufen der Methode).

- Schalten `GUID`Sie den Kontext s <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> ein und aus (durch Aufrufen der Methode).

    > [!CAUTION]
    > Stellen Sie sicher, dass Ihr VSPackage keinen Einfluss auf den Status einer vorhandenen Kontext-GUID hat, da andere VSPackages möglicherweise davon abhängen.

## <a name="example"></a>Beispiel

Das folgende Beispiel für einen VSPackage-Befehl veranschaulicht die dynamische Sichtbarkeit eines Befehls, der von Befehlskontexten verwaltet wird, ohne das VSPackage zu laden.

Der Befehl wird so eingestellt, dass er aktiviert und angezeigt wird, wenn eine Lösung vorhanden ist. das heißt, wenn eine der folgenden Befehlskontext-GUIDs aktiv ist:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Beachten Sie im Beispiel, dass jedes Befehlsflag ein separates [Befehlsflag-Element](../../extensibility/command-flag-element.md) ist.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Beachten Sie außerdem, dass jeder UI-Kontext wie folgt in einem separaten `VisibilityItem` Element angegeben werden muss.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen eines Befehls zur Symbolleiste des Projektmappen-Explorers](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dynamisches Hinzufügen von Menüelementen](../../extensibility/dynamically-adding-menu-items.md)
