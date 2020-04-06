---
title: GUIDs und IDs von Visual Studio-Symbolleisten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe42821cdacc038d767e52373d45ddd7b8954323
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708226"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUIDs und IDs von Visual Studio-Symbolleisten
In diesem Thema werden die GUID- und ID-Werte der Symbolleisten, die in der integrierten Visual Studio-Entwicklungsumgebung (IDE) enthalten sind, und der darin enthaltenen Gruppen aufgezählt. Diese Werte werden in *.vsct-Dateien* definiert, die als Teil des Visual Studio SDK installiert werden. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> Viele der für Visual Studio verfügbaren Symbolleisten sind von Visual Studio nicht definiert, und ihre GUID- und ID-Werte sind nicht öffentlich. In diesem Thema werden nur Symbolleisten aufgeführt, die in Visual Studio SDK *.vsct-Dateien* definiert sind.

 Weitere Informationen zum Arbeiten mit IDE-Objekten, die in *.vsct-Dateien* definiert sind, finden Sie unter Erweitern von [Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Die von der Visual Studio-IDE bereitgestellten `guidSHLMainMenu`Standardsymbolleisten verwenden `GUID:ID` die GUID , es sei denn, dies wird durch die Syntax anders angegeben.

## <a name="ide-toolbars"></a>IDE-Symbolleisten
 Die folgenden Symbolleisten werden von der Visual Studio-IDE bereitgestellt. Symbolleisten können angezeigt werden, indem Sie sie im Untermenü **Symbolleisten** im Menü **Extras** auswählen. Symbolleisten in Werkzeugfenstern sind in diesem Abschnitt nicht enthalten.

 Nur Gruppen können direkt von Symbolleisten absteigen. Um eine Gruppe hinzuzufügen, legen Sie das übergeordnete Element auf die GUID und DIE ID der Symbolleiste fest. Um einer Symbolleiste eine Schaltfläche hinzuzufügen, legen Sie das übergeordnete Element auf eine Gruppe auf der Symbolleiste fest.

|Symbolleiste|id|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Build|IDM_VS_TOOL_BUILD|
|Text-Editor|IDM_VS_TOOL_TEXTEDITOR|
|Debug|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Debugspeicherort|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Spezielle Symbolleisten
 Diese Symbolleisten werden von der Visual Studio-IDE definiert, dienen jedoch speziellen Funktionen und hosten keine Befehlsgruppen.

|Symbolleiste|id|
|-------------|--------|
|Befehl zum Hinzufügen|IDM_VS_TOOL_ADDCOMMAND|
|Nicht definiert|IDM_VS_TOOL_UNDEFINED|
|XML-Schema|IDM_VS_TOOL_SCHEMA|
|XML-Daten|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Gruppen auf den IDE-Symbolleisten
 Um einer Standardsymbolleiste eine Schaltfläche hinzuzufügen, legen Sie eine der folgenden Gruppen als übergeordnete Gruppe fest. Die Gruppen werden nach übergeordneten Symbolleisten sortiert.

### <a name="standard-toolbar-groups"></a>Standard-Symbolleistengruppen

|name|id|
|----------|--------|
|Speichern/Öffnen|IDG_VS_TOOLSB_SAVEOPEN|
|Ausschneiden/Kopieren|IDG_VS_TOOLSB_CUTCOPY|
|Rückgängig/Wiederholen|IDG_VS_TOOLSB_UNDOREDO|
|Ausführen/Bauen|IDG_VS_TOOLSB_RUNBUILD|
|Suchen,|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Neue Fenster|IDG_VS_TOOLSB_NEWWINDOWS|
|Laden/Speichern|IDG_VS_WINDOWUI_LOADSAVE|
|Maßstab|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Erstellen von Symbolleistengruppen

|name|id|
|----------|--------|
|Build-Bar|IDG_VS_BUILDBAR|
|Abbrechen|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Texteditor-Symbolleistengruppen

|name|id|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|Indent|IDG_VS_EDITTOOLBAR_INDENT|
|Comment|IDG_VS_EDITTOOLBAR_COMMENT|
|Lesezeichen|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Debugwerkzeugleistengruppen

|name|id|
|----------|--------|
|Ausführung|IDM_DEBUG_TOOLBAR|
|Schrittweises Ausführen|IDG_DEBUG_TOOLBAR_STEPPING|
|Überwachen|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Debugposition Symbolleistengruppen

|name|id|
|----------|--------|
|Debugspeicherort|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Symbolleisten des Toolfensters
 Symbolleisten können direkt in der IDE oder in Toolfenstern wie **dem Projektmappen-Explorer**angezeigt werden. Da Toolfenster nicht in *.vsct-Dateien* definiert sind, verfügen Toolfenster-Symbolleisten nicht über definierte Eltern. Stattdessen werden sie im Code platziert. Die folgende Tabelle zeigt die Symbolleisten, die in Symbolfenstern in der IDE angezeigt werden, sowie die darin enthaltenen Befehlsgruppen.

> [!NOTE]
> Symbolleisten und Gruppen verwenden `guidSHLMainMenu`die GUID , sofern nicht anders angegeben, indem die GUID:ID-Syntax verwendet wird. Wenn eine GUID für eine Symbolleiste angegeben ist, gilt sie auch für die Gruppen, die von dieser Symbolleiste abstammen.

|Werkzeugfenster|Symbolleiste|Gruppen|
|-----------------|-------------|------------|
|Projektmappen-Explorer|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. 5|
|Server-Explorer|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Eigenschaften|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Klassenansicht|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Klassenansicht|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Objektkatalog|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Objektkatalog|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Output|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Suchen und Ersetzen|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Suchergebnisse: 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Suchergebnisse 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Codeausschnitt|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Lesezeichen|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Aufgabenliste|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Benutzeraufgaben|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Fehlerliste|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Aufrufbrowser|IDM_VS_TOOL_CALLBROWSER1.. 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Breakpoints|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Disassemblierung|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Speicher 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1.. 4<br /><br /> IDG_MEMORY_COLUMNS1.. 4|
|Prozesse|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen eines Menücontrollers zu einer Symbolleiste](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Hinzufügen einer Symbolleiste zu einem Toolfenster](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [GUIDs und IDs von Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
