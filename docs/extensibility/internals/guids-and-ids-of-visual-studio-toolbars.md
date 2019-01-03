---
title: GUIDs und IDs der Visual Studio-Symbolleisten | Microsoft-Dokumentation
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 054f4f19d24f2751a560a3d86eae7294aa2bd7dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850900"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUIDs und IDs von Visual Studio-Symbolleiste
Dieses Thema listet die GUID und ID-Werte, der in Symbolleisten, die in der integrierten Entwicklungsumgebung (IDE) von Visual Studio enthalten sind, und der Gruppen enthalten. Diese Werte werden in definiert *VSCT* Dateien, die als Teil von Visual Studio SDK installiert werden. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Viele der in Symbolleisten in Visual Studio zur Verfügung sind nicht definiert, von Visual Studio und ihrer GUID und ID-Werte sind nicht öffentlich. Dieses Thema enthält nur die Symbolleisten, die in Visual Studio SDK definierten *VSCT* Dateien.  
  
 Weitere Informationen zum Arbeiten mit IDE-Objekten, die definiert sind *VSCT* finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Verwenden Sie die GUID die von Visual Studio-IDE bereitgestellten Standardsymbolleisten `guidSHLMainMenu`, sofern nicht anders mithilfe angegeben `GUID:ID` Syntax.  
  
## <a name="ide-toolbars"></a>IDE-Symbolleisten  
 Die folgenden Symbolleisten werden von Visual Studio-IDE bereitgestellt. Symbolleisten können angezeigt werden, indem Sie sie auf Auswählen der **Symbolleisten** Untermenü die **Tools** Menü. Symbolleisten in Toolfenstern sind nicht in diesem Abschnitt enthalten.  
  
 Nur Gruppen können direkt von Symbolleisten abgeleitet werden. Um eine Gruppe hinzuzufügen, legen Sie das übergeordnete Element auf die GUID und ID der Symbolleiste aus. Um eine Symbolleiste eine Schaltfläche hinzuzufügen, legen Sie das übergeordnete Element zu einer Gruppe auf der Symbolleiste.  
  
|Symbolleiste|ID|  
|-------------|--------|  
|Standard|IDM_VS_TOOL_STANDARD|  
|Build|IDM_VS_TOOL_BUILD|  
|Text-editor|IDM_VS_TOOL_TEXTEDITOR|  
|Debug|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Debugspeicherort|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Spezielle Symbolleisten  
 Diese Symbolleisten werden definiert, von der Visual Studio-IDE, aber sie spezielle Funktionen bereitstellen und hosten Sie Befehlsgruppen nicht.  
  
|Symbolleiste|ID|  
|-------------|--------|  
|Befehl zum Hinzufügen|IDM_VS_TOOL_ADDCOMMAND|  
|Nicht definiert|IDM_VS_TOOL_UNDEFINED|  
|XML-schema|IDM_VS_TOOL_SCHEMA|  
|XML-Daten|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>Gruppen auf dem IDE-Symbolleisten  
 Um eine standard-Symbolleiste eine Schaltfläche hinzuzufügen, legen Sie eine der folgenden Gruppen als übergeordnete Klasse aus. Die Gruppen werden von der übergeordneten Symbolleiste sortiert.  
  
### <a name="standard-toolbar-groups"></a>Standardsymbolleiste Gruppen  
  
|name|ID|  
|----------|--------|  
|Speichern/Öffnen|IDG_VS_TOOLSB_SAVEOPEN|  
|Ausschneiden/Kopieren|IDG_VS_TOOLSB_CUTCOPY|  
|Rückgängig/Wiederholen|IDG_VS_TOOLSB_UNDOREDO|  
|Führen Sie/Build|IDG_VS_TOOLSB_RUNBUILD|  
|Suchen|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|Neue windows|IDG_VS_TOOLSB_NEWWINDOWS|  
|Laden/Speichern|IDG_VS_WINDOWUI_LOADSAVE|  
|Monitor "|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>Symbolleistengruppen erstellen  
  
|name|ID|  
|----------|--------|  
|Build-Leiste|IDG_VS_BUILDBAR|  
|Abbrechen|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Text-Editor-Symbolleistengruppen  
  
|name|ID|  
|----------|--------|  
|Abschluss|IDM_VS_TOOL_TEXTEDITOR|  
|Indent|IDG_VS_EDITTOOLBAR_INDENT|  
|Kommentar|IDG_VS_EDITTOOLBAR_COMMENT|  
|Lesezeichen|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>Debug-Symbolleistengruppen  
  
|name|ID|  
|----------|--------|  
|Ausführung|IDM_DEBUG_TOOLBAR|  
|Schrittweises Ausführen|IDG_DEBUG_TOOLBAR_STEPPING|  
|Überwachen|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>Debuggen von Gruppen für Standort-Symbolleiste  
  
|name|ID|  
|----------|--------|  
|Debugspeicherort|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Symbolleisten des Toolfensters  
 Symbolleisten können angezeigt werden direkt in der IDE oder in Toolfenstern wie z. B. **Projektmappen-Explorer**. Da Toolfenster in nicht definiert sind *VSCT* sind Dateien, Symbolleisten des Toolfensters nicht übergeordneten Elementen definiert haben. Stattdessen werden diese im Code platziert. Die folgende Tabelle zeigt die Symbolleisten, die Toolfenster in der IDE angezeigt werden und die darin enthaltenen Befehlsgruppen.  
  
> [!NOTE]
>  Verwenden Sie die GUID, Symbolleisten und Gruppen `guidSHLMainMenu`, sofern nicht anders angegeben, mit der GUID: ID-Syntax. Eine GUID für eine Symbolleiste angegeben ist, gilt er auch den Gruppen, die von dieser Symbolleiste abgeleitet.  
  
|Toolfenster|Symbolleiste|Gruppen|  
|-----------------|-------------|------------|  
|Projektmappen-Explorer|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|  
|Server-Explorer|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Eigenschaften|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Klassenansicht|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Klassenansicht|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Objektkatalog|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Objektkatalog|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Output|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Suchen und Ersetzen|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Suchergebnisse: 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Suchergebnisse: 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|Codeausschnitt|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Lesezeichen|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|Aufgabenliste|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Benutzeraufgaben|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Fehlerliste|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Aufrufbrowser|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Haltepunkte|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Disassemblierung|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Arbeitsspeicher von 1 bis 4|GuidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|  
|Prozesse|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>Siehe auch  
 [Eine Symbolleiste ein Menücontroller hinzugefügt](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Hinzufügen einer Symbolleiste zu einem Toolfenster](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUIDs und IDs von Visual Studio-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)