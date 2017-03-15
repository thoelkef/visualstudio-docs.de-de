---
title: "GUIDs und IDs der Visual Studio-Symbolleisten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Gruppen"
  - "Symbolleisten"
  - "Visual Studio-Symbolleiste"
  - "ID"
  - "Toolgar-Gruppe"
  - "Symbolleiste des Toolfensters"
  - "GUID"
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# GUIDs und IDs der Visual Studio-Symbolleisten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieses Thema listet die ID\-Werte der GUID\-Wert und auf Symbolleisten, die in der integrierten Entwicklungsumgebung \(IDE\) von Visual Studio enthalten sind, und der Gruppen enthalten.  Diese Werte werden in .vsct\-Dateien definiert, die als Teil von Visual Studio SDK installiert werden.  Weitere Informationen finden Sie unter [IDE\-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Viele der Symbolleisten, die in Visual Studio verfügbar sind, werden nicht von Visual Studio definiert, und ihre GUID\-Wert und ID\-Werte sind nicht öffentlich.  In diesem Thema werden nur auf Symbolleisten, die in den Dateien von Visual Studio SDK .vsct definiert sind.  
  
 Weitere Informationen zum Arbeiten mit IDE\-Objekten, die in .vsct\-Dateien definiert werden, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md)funktioniert.  
  
 Die standardmäßige Symbolleisten, die von der Visual Studio\-IDE bereitgestellt werden, verwenden die GUID `guidSHLMainMenu`, wenn andernfalls durch die Verwendung von GUIDs: Syntax für IDs.  
  
## IDE\-Symbolleisten  
 Die folgenden Symbolleisten werden von der Visual Studio\-IDE bereitgestellt.  Symbolleisten können angezeigt werden, indem Sie sie auf dem **Symbolleisten** Untermenü des Menüs **Extras** auswählt.  Symbolleisten in Toolfenstern werden nicht in diesem Abschnitt aufgeführt.  
  
 Nur die Gruppen können direkt aus absteigen Symbolleisten.  Um eine Gruppe hinzuzufügen, legen Sie dessen übergeordnetes Element mit dem GUID und ID der Symbolleiste fest.  Um eine Schaltfläche auf einer Symbolleiste hinzugefügt werden soll, legen Sie das übergeordnete Element auf der Symbolleiste auf eine Gruppe fest.  
  
|Symbolleiste|ID|  
|------------------|--------|  
|Standard|IDM\_VS\_TOOL\_STANDARD|  
|Build|IDM\_VS\_TOOL\_BUILD|  
|Text\-Editor|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Debug|guidVSDebugGroup: IDM\_DEBUG\_TOOLBAR|  
|Multithreaded Speicherort|guidVSDebugGroup: IDM\_DEBUG\_CONTEXT\_TOOLBAR|  
  
### Besondere Symbolleisten  
 Diese Symbolleisten werden von der Visual Studio\-IDE definiert, aber sie können spezielle Funktionen und nicht Host Befehlsgruppen.  
  
|Symbolleiste|ID|  
|------------------|--------|  
|Fügen Sie dem Befehl hinzu|IDM\_VS\_TOOL\_ADDCOMMAND|  
|Nicht definiert|IDM\_VS\_TOOL\_UNDEFINED|  
|XML\-Schema|IDM\_VS\_TOOL\_SCHEMA|  
|XML\-Daten|IDM\_VS\_TOOL\_DATA|  
  
## Gruppen auf den IDE\-Symbolleisten  
 Um eine Schaltfläche eine Standardsymbolleiste hinzuzufügen, legen Sie eine der folgenden Gruppen als übergeordnetes Element fest.  Die Symbolleiste Elemente werden durch Gruppen sortiert.  
  
### Standardwert symbolleisten\-Gruppen  
  
|Name|ID|  
|----------|--------|  
|Speichern Sie öffnen\/|IDG\_VS\_TOOLSB\_SAVEOPEN|  
|Ausschneiden bzw. Kopieren|IDG\_VS\_TOOLSB\_CUTCOPY|  
|Rückgängig\/Wiederholen|IDG\_VS\_TOOLSB\_UNDOREDO|  
|Build\/Ausführung|IDG\_VS\_TOOLSB\_RUNBUILD|  
|Suche|IDG\_VS\_TOOLSB\_SEARCH|  
|Windows|IDG\_VS\_TOOLSB\_WINDOWS|  
|Das neue Fenster|IDG\_VS\_TOOLSB\_NEWWINDOWS|  
|Laden und Speichern|IDG\_VS\_WINDOWUI\_LOADSAVE|  
|Messgerät|IDG\_VS\_TOOLSB\_GAUGE|  
  
### Erstellen Sie Symbolleisten\-Gruppen  
  
|Name|ID|  
|----------|--------|  
|Erstellen von leiste|IDG\_VS\_BUILDBAR|  
|Abbrechen|IDG\_VS\_BUILD\_CANCEL|  
  
### Text\-Editor\-Symbolleisten\-Gruppen  
  
|Name|ID|  
|----------|--------|  
|Abschluss|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Indent|IDG\_VS\_EDITTOOLBAR\_INDENT|  
|Kommentar|IDG\_VS\_EDITTOOLBAR\_COMMENT|  
|Lesezeichen|IDG\_VS\_EDITTOOLBAR\_TEMPBOOKMARKS|  
  
### Debuggen von Symbolleisten\-Gruppen  
  
|Name|ID|  
|----------|--------|  
|Ausführung|IDM\_DEBUG\_TOOLBAR|  
|Schrittweises Ausführen|IDG\_DEBUG\_TOOLBAR\_STEPPING|  
|Watch|IDG\_DEBUG\_TOOLBAR\_WATCH|  
|Windows|IDG\_DEBUG\_TOOLBAR\_WINDOWS|  
  
### Debuggen Speicherort\-Symbolleisten\-Gruppen  
  
|Name|ID|  
|----------|--------|  
|Multithreaded Speicherort|IDG\_DEBUG\_CONTEXT\_TOOLBAR|  
  
## Tool\-Fenster\-Symbolleisten  
 Symbolleisten können direkt in der IDE oder in Toolfenstern wie **Projektmappen\-Explorer**angezeigt werden.  Da Toolfenster nicht in .vsct\-Dateien definiert, Toolfenster symbolleisten haben keine übergeordneten Elemente definiert sind.  Stattdessen werden sie in den Code eingefügt.  In der folgenden Tabelle sind die Symbolleisten, die ein Toolfenster in der IDE angezeigt werden, und die Befehlsgruppen an.  
  
> [!NOTE]
>  Symbolleisten und Gruppen verwenden die GUID `guidSHLMainMenu`, wenn andernfalls durch die Verwendung von GUIDs: Syntax für IDs.  Wo eine GUID für eine Symbolleiste angegeben wird, gilt es auch an die Gruppen, die von dieser Symbolleiste absteigen.  
  
|Toolfenster|Symbolleiste|Gruppen|  
|-----------------|------------------|-------------|  
|Projektmappen\-Explorer|IDM\_VS\_TOOL\_PROJWIN|IDG\_VS\_PROJ\_TOOLBAR1..5|  
|Server\-Explorer|guid\_SE\_MenuGroup: IDM\_SE\_TOOLBAR\_SERVEREXPLORER|IDG\_SE\_TOOLBAR\_REFRESH|  
|Eigenschaften|IDM\_VS\_TOOL\_PROPERTIES|IDG\_VS\_PROPERTIES\_SORT<br /><br /> IDG\_VS\_PROPERTIES\_PAGES|  
|Klassenansicht|IDM\_VS\_TOOL\_CLASSVIEW|IDG\_VS\_CLASSVIEW\_FOLDERS<br /><br /> IDG\_VS\_CLASSVIEW\_SEARCH<br /><br /> IDG\_VS\_CLASSVIEW\_SETTINGS|  
|Klassenansicht|IDM\_VS\_TOOL\_CLASSVIEW\_GO|IDG\_VS\_CLASSVIEW\_SEAR CH2|  
|Objektkatalog|IDM\_VS\_TOOL\_OBJBROWSER|IDG\_VS\_OBJBROWSER\_SUBSETS<br /><br /> IDG\_VS\_OBJBROWSER\_SEARCH<br /><br /> IDG\_VS\_OBJBROWSER\_ADDREFERENCE<br /><br /> IDG\_VS\_OBJBROWSER\_BROWSERSETTINGS|  
|Objektkatalog|IDM\_VS\_TOOL\_OBJECT\_BROWSER\_GO|IDG\_VS\_OBJBROWSER\_SEAR CH2|  
|Output|IDM\_VS\_TOOL\_OUTPUTWINDOW|IDG\_VS\_OUTPUTWINDOW\_SELECT<br /><br /> IDG\_VS\_OUTPUTWINDOW\_GOTO<br /><br /> IDG\_VS\_OUTPUTWINDOW\_NEXTPREV<br /><br /> IDG\_VS\_OUTPUTWINDOW\_CLEAR<br /><br /> IDG\_VS\_OUTPUTWINDOW\_WORDWRAP|  
|Suchen und Ersetzen|IDM\_VS\_TOOL\_UNIFIEDFIND|IDG\_VS\_FINDTAB<br /><br /> IDG\_VS\_REPLACETAB|  
|Suchergebnisse: 1|IDM\_VS\_TOOL\_FINDRESULTS1|IDG\_VS\_FINDRESULTS1\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS1\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS1\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS1\_STOPFIND|  
|Suchergebnisse: 2|IDM\_VS\_TOOL\_FINDRESULTS2|IDG\_VS\_FINDRESULTS2\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS2\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS2\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS2\_STOPFIND|  
|Snippet|IDM\_VS\_TOOL\_SNIPPETMENUS|IDG\_VS\_SNIPPET\_REPL<br /><br /> IDG\_VS\_SNIPPET\_REF<br /><br /> IDG\_VS\_SNIPPET\_PROP|  
|Lesezeichen|IDM\_VS\_TOOL\_BOOKMARKWIND|IDG\_VS\_BWNEWFOLDER<br /><br /> IDG\_VS\_BWNEXTBM<br /><br /> IDG\_VS\_BWNEXTBMF<br /><br /> IDG\_VS\_BWENABLE<br /><br /> IDG\_VS\_BWDELETE|  
|Aufgabenliste|IDM\_VS\_TOOL\_TASKLIST|IDG\_VS\_TASKLIST\_PROVIDERLIST|  
|Benutzeraufgaben|IDM\_VS\_TOOL\_USERTASKS|IDG\_VS\_TASKLIST\_PROVIDERLIST<br /><br /> IDG\_VS\_USERTASKS\_EDIT|  
|Fehlerliste|IDM\_VS\_TOOL\_ERRORLIST|IDG\_VS\_ERRORLIST\_ERRORGROUP<br /><br /> IDG\_VS\_ERRORLIST\_WARNINGGROUP<br /><br /> IDG\_VS\_ERRORLIST\_MESSAGEGROUP|  
|Aufrufs\-Browser|IDM\_VS\_TOOL\_ CALLBROWSER1. .16|\_ACTIONS IDG\_VS\_TOOLBAR\_ CALLBROWSER1<br /><br /> \_TYPE IDG\_VS\_TOOLBAR\_ CALLBROWSER1<br /><br /> \_CBSETTINGS IDG\_VS\_TOOLBAR\_ CALLBROWSER1|  
|Haltepunkte|guidVSDebugGroup: IDM\_BREAKPOINTS\_WINDOW\_TOOLBAR|IDG\_BREAKPOINTS\_WINDOW\_NEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_DELETE<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_ALL<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_VIEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_EDIT<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_COLUMNS|  
|Disassembly|guidVSDebugGroup: IDM\_DISASM\_WINDOW\_TOOLBAR|IDG\_DISASM\_WINDOW\_TOOLBAR|  
|1\-4 Arbeitsspeicher|guidVSDebugGroup: IDM\_MEMORY\_WINDOW\_TOOLBAR1… 4|IDG\_MEMORY\_EXPRESSION1..4<br /><br /> IDG\_MEMORY\_ COLUMNS1. .4|  
|Prozesse|guidVSDebugGroup: IDM\_ATTACHED\_PROCS\_TOOLBAR|IDG\_ATTACHED\_PROCS\_EXECCNTRL IDG\_ATTACHED\_PROCS\_STEPPING<br /><br /> IDG\_ATTACHED\_PROCS\_EXE CCNTRL2<br /><br /> IDG\_ATTACHED\_PROCS\_ATTACH<br /><br /> IDG\_ATTACHED\_PROCS\_COLUMNS|  
  
## Siehe auch  
 [Hinzufügen eines Controllers im Menü auf einer Symbolleiste](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Ein Toolfenster hinzugefügt eine Symbolleiste](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUIDs und IDs der Visual Studio\-Menüs](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)