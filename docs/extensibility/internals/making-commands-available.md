---
title: Verfügbarmachen von Befehlen | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 88f29f575cc59b365978376f01f53f2624c31cd0
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="making-commands-available"></a>Verfügbarmachen von Befehlen
Wenn mehrere VSPackages zu Visual Studio hinzugefügt werden, kann die Benutzeroberfläche (UI) mit Befehlen Akzente werden. Sie können das Paket aus, um dieses Problem wie folgt zu reduzieren Programmieren:

-   Programm, das Paket, damit sie geladen wird, nur wenn ein Benutzer ist es erforderlich.

-   Programmieren Sie das Paket so, dass seine Befehle angezeigt werden, nur, wenn sie im Kontext des aktuellen Zustands der integrierten Entwicklungsumgebung (IDE) erforderlich sein können.

## <a name="delayed-loading"></a>Verzögertes Laden
 Die gewohnte Weise So aktivieren Sie ist das VSPackage so entwerfen, dass die Befehle in der Benutzeroberfläche angezeigt werden, aber das Paket selbst nicht geladen werden, wird bis ein Benutzer auf einen der Befehle klickt verzögertes Laden. Erstellen Sie dazu in der VSCT-Datei Befehlen, die keine Befehlsflags verfügen.

 Das folgende Beispiel zeigt die Definition eines Menübefehls aus einer VSCT-Datei. Dies ist der Befehl, der von der Visual Studio-Paket-Vorlage generiert wird bei der **Menübefehl** in der Vorlage ausgewählt ist.

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

 Im Beispiel wenn die übergeordnete Gruppe `MyMenuGroup`, ist ein untergeordnetes Element eines Menüs der obersten Ebene wie die **Tools** im Menü der Befehl werden auf das Menü angezeigt, aber das Paket, das der Befehl ausgeführt wird nicht geladen werden, bis der Befehl geklickt wird durch einen Benutzer. Doch durch Programmieren den Befehl zum Implementieren der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle, damit Sie das Paket geladen werden, wenn das Menü, das den Befehl enthält zunächst erweitert wird.

 Beachten Sie, dass das verzögertes Laden auch verlangsamten verbessern kann.

## <a name="current-context-and-the-visibility-of-commands"></a>Aktuellen Kontext und die Sichtbarkeit von Befehlen
 Sie können programmieren, VSPackage-Befehle werden sichtbar oder ausgeblendet, je nach den aktuellen Status des VSPackage Daten oder die Aktionen, die derzeit relevant sind. Sie können das VSPackage zum Festlegen des Status der darin enthaltenen Befehle in der Regel mit einer Implementierung von der <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> Methode aus der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Schnittstelle, aber dies erfordert das VSPackage geladen werden soll, bevor der Code ausgeführt werden kann. Stattdessen wird empfohlen, dass Sie der IDE an, um die Sichtbarkeit der Befehle zu verwalten, ohne das Laden des Pakets aktivieren. Ordnen Sie dazu in der VSCT-Datei eine oder mehrere spezielle Benutzeroberfläche Kontexten Befehle. Dieser Kontexte Benutzeroberfläche sind durch eine GUID identifiziert als bezeichnet eine *Befehlskontext GUID*.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überwacht die Änderungen, die sich aus Benutzeraktionen z. B. das Laden eines Projekts ist oder Sie bearbeiten, Erstellen von ergeben. Wenn Änderungen auftreten, wird die Darstellung der IDE automatisch geändert. Die folgende Tabelle zeigt die vier wichtigsten Kontexte der IDE ändern, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] überwacht.

|Typ des Kontexts|Beschreibung|
|---------------------|-----------------|
|Aktive Projekttyp|Für die meisten Projekttypen dies `GUID` Wert ist identisch mit der GUID des VSPackage, das das Projekt implementiert. Allerdings [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Projekte verwenden den Projekttyp `GUID` als Wert.|
|Aktives Fenster|In der Regel ist dies die letzte aktive Fenster, das die aktuellen UI-Kontext für tastenbindungen herstellt. Jedoch kann er auch eines Toolfensters sein, eine schlüsselbindung-Tabelle, die den internen Webbrowser ähnelt. Für Registerkarten Dokumentfenster z. B. den HTML-Editor, jede Registerkarte verfügt über einen anderen Befehlskontext `GUID`.|
|Active-Sprachdienst|Der Sprachdienst, die der Datei zugeordnet ist, die derzeit in einem Text-Editor angezeigt wird.|
|Aktives Toolfenster|Ein Toolfenster, die geöffnet ist und den Fokus hat.|

 Eine fünfte wichtigen Kontextbereich ist der Zustand der Benutzeroberfläche der IDE. Benutzeroberflächen-Kontexte prognostiziert nach aktiven Befehlskontext `GUID`s, wie folgt:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

 Diese GUIDs werden als aktiv oder inaktiv ist, abhängig von den aktuellen Status der IDE markiert. Mehrere UI-Kontexte können gleichzeitig aktiv sein.

### <a name="hiding-and-displaying-commands-based-on-context"></a>Ausblenden und Anzeigen von Befehlen, die anhand des Kontexts
 Sie können ein- oder Ausblenden von einem Paket-Befehl in der IDE ohne Laden des Pakets selbst. Zu diesem Zweck definieren Sie den Befehl in der VSCT-Datei des Pakets mithilfe der `DefaultDisabled`, `DefaultInvisible`, und `DynamicVisibility` Befehl Flags und Hinzufügen von einem oder mehreren [VisibilityItem](../../extensibility/visibilityitem-element.md) Elemente, die die [ VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) Abschnitt. Wenn eine angegebene Befehlskontext `GUID` wird aktiv ist, wird der Befehl ohne Laden des Pakets angezeigt.

### <a name="custom-context-guids"></a>Benutzerdefinierten Kontext-GUIDs
 Wenn einen entsprechenden Befehl-Kontext, den GUID noch nicht definiert ist, können Sie in Ihrem VSPackage definieren und Programmieren Sie es als aktiv oder inaktiv nach Bedarf, um die Sichtbarkeit der Befehle zu steuern. Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Service:

-   Registrieren Sie die Kontext-GUIDs (durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> Methode).

-   Abrufen des Status eines Kontexts `GUID` (durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode).

-   Aktivieren Sie Kontext `GUID`s ein- und ausschalten (durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> Methode).

    > [!CAUTION]
    > Stellen Sie sicher, dass Ihr VSPackage da anderen VSPackages davon abhängig sind, möglicherweise nicht den Status von keinem vorhandenen Kontext GUID auswirkt.

## <a name="example"></a>Beispiel
 Ein VSPackage-Befehl im folgende Beispiel wird veranschaulicht, die dynamische Sichtbarkeit eines Befehls, der vom Befehl Kontexten verwaltet wird, ohne zu laden das VSPackage.

 Der Befehl festgelegt ist, werden aktiviert, und dann angezeigt, wenn eine Projektmappe vorhanden ist; d. h., wenn eine der folgenden Befehlskontext GUIDs aktiv ist:

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_EmptySolution>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasMultipleProjects>

-   <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionHasSingleProject>

Im Beispiel beachten Sie, dass jeder Befehlsflag eine Separate [Befehlsflag](../../extensibility/command-flag-element.md) Element.

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

Beachten Sie auch, die jede Benutzeroberflächenkontext muss, in einer separaten zugeordnet werden `VisibilityItem` -Element wie folgt.

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

- [MenuCommands im Vergleich zu OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dynamisches Hinzufügen von Menüelementen](../../extensibility/dynamically-adding-menu-items.md)