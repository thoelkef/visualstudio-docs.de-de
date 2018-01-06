---
title: GUIDs und IDs der Visual Studio-Symbolleisten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bbb14818cebb35f703ec6f5ade084d96ac383d6a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUIDs und IDs der Visual Studio-Symbolleisten
Dieses Thema listet die GUID und ID-Werte der Symbolleisten, die in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthalten sind, und der Gruppen enthalten. Diese Werte werden in der VSCT-Dateien definiert, die als Teil der Visual Studio-SDK installiert sind. Weitere Informationen finden Sie unter [IDE-Defined Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Viele der Symbolleisten für Visual Studio verfügbar sind nicht durch Visual Studio, und die entsprechenden GUID-Werte definiert und ID-Werte sind nicht öffentlich. Dieses Thema listet nur die Symbolleisten, die in Visual Studio SDK VSCT-Dateien definiert werden.  
  
 Weitere Informationen zum Arbeiten mit IDE-Objekte, die in der VSCT-Dateien definiert sind, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Verwenden Sie die GUID die von der Visual Studio-IDE bereitgestellten Standardsymbolleisten `guidSHLMainMenu`, anders angegeben mit GUID: ID-Syntax.  
  
## <a name="ide-toolbars"></a>IDE-Symbolleisten  
 Die folgenden Symbolleisten werden von der Visual Studio-IDE bereitgestellt. Symbolleisten können angezeigt werden, indem Sie sie auf Auswählen der **Symbolleisten** Untermenü die **Tools** Menü. Symbolleisten in Toolfenstern sind nicht in diesem Abschnitt enthalten.  
  
 Nur Gruppen können direkt von Symbolleisten abgeleitet werden. Legen Sie zum Hinzufügen einer Gruppe seinem übergeordneten Element, auf die GUID und die ID der Symbolleiste. Um eine Symbolleiste eine Schaltfläche hinzuzufügen, legen Sie das übergeordnete Element zu einer Gruppe auf der Symbolleiste.  
  
|Symbolleiste|Id|  
|-------------|--------|  
|Standard|IDM_VS_TOOL_STANDARD|  
|Build|IDM_VS_TOOL_BUILD|  
|Text-Editor|IDM_VS_TOOL_TEXTEDITOR|  
|Debug|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Debugspeicherort|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Spezielle Symbolleisten  
 Diese Symbolleisten von Visual Studio-IDE definiert sind, dienen aber spezielle Funktionen und Hosten Befehlsgruppen nicht.  
  
|Symbolleiste|Id|  
|-------------|--------|  
|Befehl hinzufügen|IDM_VS_TOOL_ADDCOMMAND|  
|Nicht definiert|IDM_VS_TOOL_UNDEFINED|  
|XML-Schema|IDM_VS_TOOL_SCHEMA|  
|XML-Daten|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>Gruppen auf dem IDE-Symbolleisten  
 Um eine Standardsymbolleiste eine Schaltfläche hinzuzufügen, legen Sie eine der folgenden Gruppen wie das übergeordnete Objekt. Die Gruppen werden von der übergeordneten Symbolleiste sortiert.  
  
### <a name="standard-toolbar-groups"></a>Standardsymbolleiste Gruppen  
  
|name|Id|  
|----------|--------|  
|Speichern/Öffnen|IDG_VS_TOOLSB_SAVEOPEN|  
|Ausschneiden/Kopieren|IDG_VS_TOOLSB_CUTCOPY|  
|Rückgängig/Wiederholen|IDG_VS_TOOLSB_UNDOREDO|  
|Ausführen/Build|IDG_VS_TOOLSB_RUNBUILD|  
|Suchen|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|Neue Fenster|IDG_VS_TOOLSB_NEWWINDOWS|  
|Laden/Speichern|IDG_VS_WINDOWUI_LOADSAVE|  
|Messgerät|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>Symbolleistengruppen erstellen  
  
|name|Id|  
|----------|--------|  
|Build-Leiste|IDG_VS_BUILDBAR|  
|Abbrechen|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Text-Editor-Symbolleiste Gruppen  
  
|name|Id|  
|----------|--------|  
|Abschluss|IDM_VS_TOOL_TEXTEDITOR|  
|Indent|IDG_VS_EDITTOOLBAR_INDENT|  
|Kommentar|IDG_VS_EDITTOOLBAR_COMMENT|  
|Lesezeichen|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>Debug-Symbolleistengruppen  
  
|name|Id|  
|----------|--------|  
|Ausführung|IDM_DEBUG_TOOLBAR|  
|Schrittweises Ausführen|IDG_DEBUG_TOOLBAR_STEPPING|  
|Überwachen|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>Debuggen Sie die Symbolleistengruppen Speicherort  
  
|name|Id|  
|----------|--------|  
|Debugspeicherort|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Symbolleisten des Toolfensters  
 Symbolleisten können angezeigt werden direkt in der IDE oder in Toolfenstern wie z. B. **Projektmappen-Explorer**. Da Toolfenster nicht in der VSCT-Dateien definiert sind, führen Sie Symbolleisten des Toolfensters nicht definierten übergeordneten Objekte verfügen. Stattdessen werden sie im Code platziert. Die folgende Tabelle zeigt die Symbolleisten, die Toolfenster in der IDE angezeigt werden, und die darin enthaltenen Befehlsgruppen.  
  
> [!NOTE]
>  Verwenden Sie die GUID, Symbolleisten und Gruppen `guidSHLMainMenu`, anders angegeben mit GUID: ID-Syntax. Eine GUID für eine Symbolleiste angegeben ist, gelten auch für die Gruppen, die über diese Symbolleiste abgeleitet werden.  
  
|Toolfenster|Symbolleiste|Gruppen|  
|-----------------|-------------|------------|  
|Projektmappen-Explorer|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|  
|Server-Explorer|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Eigenschaften|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Klassenansicht|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Klassenansicht|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Objektkatalog|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Objektkatalog|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Ausgabe|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Suchen und Ersetzen|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Suchergebnisse: 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Suchen Sie Ergebnisse: 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|Codeausschnittauswahl|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Lesezeichen|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|Aufgabenliste|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Benutzeraufgaben|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Fehlerliste|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Aufrufbrowser|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Haltepunkte|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Disassemblierung|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Speicher 1 bis 4|GuidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|  
|Prozesse|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>Siehe auch  
 [Eine Symbolleiste hinzugefügt ein Menücontroller](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Ein Toolfenster hinzugefügt eine Symbolleiste](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUIDs und IDs der Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)