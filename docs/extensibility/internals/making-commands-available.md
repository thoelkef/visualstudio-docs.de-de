---
title: Verfügbarmachen von Befehlen | Microsoft-Dokumentation
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a14998b8dca3c14bdae4f00f1940c19b696646ff
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231856"
---
# <a name="making-commands-available"></a>Verfügbarmachen von Befehlen

Wenn mehrere VSPackages zu Visual Studio hinzugefügt werden, kann die Benutzeroberfläche (UI) mit den Befehlen Akzente werden. Sie können das Paket, um dieses Problem lautet wie folgt zu reduzieren, Programmieren:

- Programm des Pakets, damit sie geladen wird, nur wenn ein Benutzer ist erforderlich.

- Programmieren Sie das Paket so, dass die Befehle nur angezeigt werden, wenn diese im Kontext des aktuellen Zustands der integrierten Entwicklungsumgebung (IDE) werden möglicherweise benötigt.

## <a name="delayed-loading"></a>Verzögertes Laden

Das übliche Verfahren zum ermöglichen ist das VSPackage so entwerfen, dass die Befehle werden in der Benutzeroberfläche angezeigt, aber das Paket selbst nicht geladen werden, wird bis ein Benutzer, einen der Befehle klickt das verzögerte Laden. Erstellen Sie dazu in der VSCT-Datei Befehle, die keine Befehlsflags.

Das folgende Beispiel zeigt die Definition eines Menübefehls in einer VSCT-Datei. Dies ist der Befehl, der von der Visual Studio-Paketvorlage generiert wird bei der **Menübefehl** in der Vorlage ausgewählt ist.

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

Im Beispiel wenn der übergeordneten Gruppe `MyMenuGroup`, ist ein untergeordnetes Element eines Menüs der obersten Ebene wie die **Tools** im Menü der Befehl wird auf diesem Menü angezeigt werden, aber das Paket, das der Befehl ausgeführt wird nicht geladen werden, bis der Befehl geklickt wird durch einen Benutzer. Doch durch die Programmierung des Befehls zum Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle, damit Sie das Paket geladen werden, wenn das Menü, das den Befehl enthält zunächst erweitert wird.

Beachten Sie, dass das verzögertes Laden auch die startleistung verbessern kann.

## <a name="current-context-and-the-visibility-of-commands"></a>Aktuelle Kontext und die Sichtbarkeit von Befehlen

Sie können programmieren, dass VSPackage Befehle sein sichtbar oder ausgeblendet ist, abhängig vom aktuellen Zustand der VSPackage-Daten oder die Aktionen, die derzeit relevant sind. Sie können das VSPackage, um den Status der darin enthaltenen Befehle, in der Regel festgelegt werden, indem eine Implementierung von der <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> Methode aus der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle, aber dies erfordert das VSPackage geladen werden, bevor sie den Code ausgeführt werden kann. Stattdessen empfehlen wir, dass Sie die IDE die Sichtbarkeit der Befehle zu verwalten, ohne das Laden des Pakets aktivieren. Ordnen Sie dazu in der VSCT-Datei eine oder mehrere spezielle Benutzeroberfläche-Kontexte Befehle. Diese Benutzeroberfläche-Kontexte werden durch eine GUID, die als bekannt identifiziert eine *Befehlskontext-GUID*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überwacht die Änderungen, die sich aus Benutzeraktionen wie das Laden eines Projekts oder die Bearbeitung von Erstellen von ergeben. Wenn Änderungen auftreten, wird die Darstellung der IDE automatisch geändert. Die folgende Tabelle zeigt die vier wichtigsten Kontexte der IDE ändern, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überwacht.

| Typ des Kontexts | Beschreibung |
|-------------------------| - |
| Aktive Projekttyp | Für die meisten Projekttypen dies `GUID` Wert ist identisch mit der GUID des VSPackage, die das Projekt implementiert. Allerdings [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte verwenden den Projekttyp `GUID` als Wert. |
| Des aktiven Fensters | In der Regel ist dies die letzte aktive Fenster, das die aktuellen UI-Kontext für tastenbindungen herstellt. Allerdings kann er auch eines Toolfensters sein, eine schlüsselbindungstabellen, die den internen Webbrowser ähnelt. Für Windows wie z. B. die HTML-Editor-Dokument mit mehreren Registerkarten jede Registerkarte verfügt über einen anderen Befehlskontext `GUID`. |
| Aktive Sprachdienst | Der Sprachdienst, der der Datei zugeordnet ist, die derzeit in einem Text-Editor angezeigt wird. |
| Aktives Toolfenster | Ein Toolfenster, das geöffnet ist und den Fokus besitzt. |

Eine fünfte wichtigen Kontextbereich wird der Zustand der Benutzeroberfläche der IDE. Benutzeroberfläche-Kontexte werden vom aktiven Befehlskontext identifiziert `GUID`s, wie folgt:

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

Diese GUIDs werden als aktiv oder inaktiv ist, je nach den aktuellen Zustand der IDE markiert. Mehrere UI-Kontext können gleichzeitig aktiv sein.

### <a name="hide-and-display-commands-based-on-context"></a>Aus- und Einblenden von Befehlen, die anhand des Kontexts

Sie können ein- oder Ausblenden von einem paketbefehl in der IDE ohne Laden des Pakets selbst. Zu diesem Zweck definieren Sie den Befehl in der VSCT-Datei des Pakets mithilfe der `DefaultDisabled`, `DefaultInvisible`, und `DynamicVisibility` Befehl Flags und Hinzufügen einer oder mehrerer [VisibilityItem](../../extensibility/visibilityitem-element.md) Elementen, die die [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) Abschnitt. Wenn eine angegebene Befehlskontext `GUID` wird aktiv ist, wird der Befehl ohne das Laden des Pakets angezeigt.

### <a name="custom-context-guids"></a>Benutzerdefinierten Kontext-GUIDs

Wenn einen entsprechenden Befehl-Kontext, den GUID noch nicht definiert ist, können Sie eine solche im VSPackage definieren, und klicken Sie dann Programmieren zu aktiven oder inaktiven nach Bedarf, um die Sichtbarkeit Ihrer Befehle zu steuern. Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> -Dienst:

- Registrieren Sie die Kontext-GUIDs (durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode).

- Abrufen des Status eines Kontexts `GUID` (durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode).

- Aktivieren von Kontext `GUID`s ein- und ausschalten (durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode).

    > [!CAUTION]
    > Stellen Sie sicher, dass das VSPackage nicht den Status der alle vorhandenen Kontext-GUID auswirkt, da andere VSPackages möglicherweise von ihnen abhängig sind.

## <a name="example"></a>Beispiel

Ein VSPackage-Befehl im folgende Beispiel wird veranschaulicht, die dynamische Sichtbarkeit eines Befehls, der von befehlskontexte verwaltet wird, ohne dass das VSPackage geladen wird.

Der Befehl festgelegt ist, werden aktiviert, und dann angezeigt, wenn eine Projektmappe vorhanden ist; Das heißt, jedes Mal, wenn eine der folgenden Befehlskontext GUIDs aktiv ist:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

Im Beispiel beachten Sie, dass jede Befehlsflag ein separates [Befehlsflag](../../extensibility/command-flag-element.md) Element.

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

Beachten Sie auch, mit dem alle UI-Kontext in einer separaten muss `VisibilityItem` -Element wie folgt.

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

## <a name="see-also"></a>Siehe auch

- [Hinzufügen eines Befehls auf der Symbolleiste des Projektmappen-Explorer](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [MenuCommands im Vergleich zu OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dynamisches Hinzufügen von Menüelementen](../../extensibility/dynamically-adding-menu-items.md)
