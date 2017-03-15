---
title: "GUIDs und IDs der Visual Studio-Men&#252;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio-Menüs"
  - "Visual Studio-Gruppen"
  - "ID"
  - "vorhandenen Menüs"
  - "GUID"
  - "Menüs"
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# GUIDs und IDs der Visual Studio-Men&#252;s
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieses Thema listet die GUID und ID\-Werte der Gruppen in der Visual Studio\-Menüleiste und Menüs. Diese Werte werden in der VSCT\-Dateien definiert, die als Teil der Visual Studio\-SDK installiert sind. Weitere Informationen finden Sie unter [IDE\-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Weitere Informationen zum Arbeiten mit integrated Development Environment, \(IDE\) Objekte, die in der VSCT\-Dateien definiert sind, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Verwenden Sie die GUID, die Menüs und Gruppen in der Visual Studio\-Menüleiste `guidSHLMainMenu`. Die Menüleiste selbst hat eine ID von `IDM_VS_TOOL_MAINMENU`.  
  
## Gruppen in der Visual Studio\-Menüleiste  
 Um ein Menü auf der Menüleiste hinzuzufügen, legen Sie eine dieser Gruppen als übergeordnetes Element.  
  
|Gruppieren|ID|  
|----------------|--------|  
|Datei\/Bearbeitungsansicht|IDG\_VS\_MM\_FILEEDITVIEW|  
|Umgestaltung|IDG\_VS\_MM\_REFACTORING:|  
|Projekt|IDG\_VS\_MM\_PROJECT|  
|Build|IDG\_VS\_MM\_BUILDDEBUGRUN|  
|Format\-Tools|IDG\_VS\_MM\_TOOLSADDINS|  
|Fenster\/Help\/Community|IDG\_VS\_MM\_WINDOWHELP|  
|Add\-Ins|IDG\_VS\_MM\_MACROS|  
|FullScreenBar|IDG\_VS\_MM\_FULLSCREENBAR|  
  
## Menüs in der Visual Studio\-Menüleiste  
 Zum Hinzufügen einer Gruppe zu einem vorhandenen Visual Studio\-Menü legen Sie eine der folgenden Menüs als übergeordnetes Element. Untermenüs werden in dieser Liste nicht enthalten.  
  
|Menü|ID|  
|----------|--------|  
|Datei|IDM\_VS\_MENU\_FILE|  
|Bearbeiten|IDM\_VS\_MENU\_EDIT|  
|Ansicht|IDM\_VS\_MENU\_VIEW|  
|Umgestalten|IDM\_VS\_MENU\_REFACTORING|  
|Projekt|IDM\_VS\_MENU\_PROJECT|  
|Build|IDM\_VS\_MENU\_BUILD|  
|Format|IDM\_VS\_MENU\_FORMAT|  
|Tools|IDM\_VS\_MENU\_TOOLS|  
|Fenster|IDM\_VS\_MENU\_WINDOW|  
|Add\-Ins|IDM\_VS\_MENU\_ADDINS|  
|Community|IDM\_VS\_MENU\_COMMUNITY|  
|Hilfe|IDM\_VS\_MENU\_HELP|  
  
## Gruppen auf Visual Studio\-Menüs  
 Im folgenden aufgeführt werden der Gruppen, die direkt von Menüs in der Visual Studio\-Menüleiste abstammen. Die schnellste Methode zum Hinzufügen eines Befehls zu einem Visual Studio\-Menü ist einer dieser Gruppen als übergeordnetes Element festgelegt. Gruppen, die alle Untermenüs werden in diesem Abschnitt nicht angezeigt.  
  
### Menü\-Dateigruppen  
  
|Gruppieren|ID|  
|----------------|--------|  
|Neue\/öffnen|IDG\_VS\_FILE\_FILE|  
|Hinzufügen|IDG\_VS\_FILE\_ADD|  
|Lösung|IDG\_VS\_FILE\_SOLUTION|  
|Sonstiges|IDG\_VS\_FILE\_MISC|  
|Speichern|IDG\_VS\_FILE\_SAVE|  
|Umbenennen|IDG\_VS\_FILE\_RENAME|  
|Browser|IDG\_VS\_FILE\_BROWSER|  
|Print|IDG\_VS\_FILE\_PRINT|  
|Zuletzt verwendet|IDG\_VS\_FILE\_MRU|  
|Verschieben|IDG\_VS\_FILE\_MOVE|  
|Beenden|IDG\_VS\_FILE\_EXIT|  
  
### Im Menü Bearbeiten  
  
|Gruppieren|ID|  
|----------------|--------|  
|Rückgängig\/Wiederholen|IDG\_VS\_EDIT\_UNDOREDO|  
|Ausschneiden, kopieren und einfügen|IDG\_VS\_EDIT\_CUTCOPY|  
|Auswählen|IDG\_VS\_EDIT\_SELECT|  
|GoTo|IDG\_VS\_EDIT\_GOTO|  
|Find|IDG\_VS\_EDIT\_FIND|  
|erzwingen|IDG\_VS\_EDIT\_OBJECTS|  
|OLE\-Verben|IDG\_VS\_EDIT\_OLEVERBS|  
|Befehl auch|IDG\_VS\_EDIT\_COMMANDWELL|  
  
### Umgestalten von Menügruppen  
  
|Gruppieren|ID|  
|----------------|--------|  
|Allgemein|IDG\_REFACTORING\_COMMON|  
|Erweitert|IDG\_REFACTORING\_ADVANCED|  
  
### Menügruppen anzeigen  
  
|Gruppieren|ID|  
|----------------|--------|  
|Formularcode|IDG\_VS\_VIEW\_FORMCODE|  
|Browser|IDG\_VS\_VIEW\_BROWSER|  
|Definieren von Ansichten|IDG\_VS\_VIEW\_DEFINEVIEWS|  
|Windows|IDG\_VS\_VIEW\_WINDOWS|  
|Architektur von Windows|IDG\_VS\_VIEW\_ARCH\_WINDOWS|  
|Organisation Windows|IDG\_VS\_VIEW\_ORG\_WINDOWS|  
|Code\-Browser|IDG\_VS\_VIEW\_CODEBROWSENAV\_WINDOWS|  
|Windows dev|IDG\_VS\_VIEW\_DEV\_WINDOWS|  
|Symbolleisten|IDG\_VS\_VIEW\_TOOLBARS|  
|Symbole|IDG\_VS\_VIEW\_SYMBOLNAVIGATE|  
|Navigieren|IDG\_VS\_VIEW\_NAVIGATE|  
|Kleine navigieren|IDG\_VS\_VIEW\_SMALLNAVIGATE|  
|Objektkatalog|IDG\_VS\_VIEW\_OBJBRWSR|  
|Befehl auch|IDG\_VS\_VIEW\_COMMANDWELL|  
|Eigenschaftenseiten|IDG\_VS\_VIEW\_PROPPAGES|  
|Aktualisieren|IDG\_VS\_VIEW\_REFRESH|  
  
### Projektgruppen\-Menü  
  
|Gruppieren|ID|  
|----------------|--------|  
|Sonstige hinzufügen|IDG\_VS\_PROJ\_MISCADD|  
|Hinzufügen|IDG\_VS\_PROJ\_ADD|  
|Ordner|IDG\_VS\_PROJ\_FOLDER|  
|Laden\/Entladen|IDG\_VS\_PROJ\_UNLOADRELOAD|  
|Verweis|IDG\_VS\_PROJ\_REFERENCE|  
|Optionen|IDG\_VS\_PROJ\_OPTIONS|  
|Einstellungen|IDG\_VS\_PROJ\_SETTINGS|  
  
### Erstellen von Menügruppen  
  
|Gruppieren|ID|  
|----------------|--------|  
|Lösung|IDG\_VS\_BUILD\_SOLUTION|  
|Auswahl|IDG\_VS\_BUILD\_SELECTION|  
|Profilgesteuerte Optimierung|IDG\_VS\_PGO\_SELECTION|  
|Sonstiges|IDG\_VS\_BUILD\_MISC|  
|Abbrechen|IDG\_VS\_BUILD\_CANCEL|  
  
### Menügruppen Tools  
  
|Gruppieren|ID|  
|----------------|--------|  
|Befehlszeile|IDG\_VS\_TOOLS\_CMDLINE|  
|Codeausschnitte|IDG\_VS\_TOOLS\_SNIPPETS|  
|Objekt\-Teilmenge|IDG\_VS\_TOOLS\_OBJSUBSET|  
|Optionen|IDG\_VS\_TOOLS\_OPTIONS|  
|Andere 2|IDG\_VS\_TOOLS\_OTHER2|  
|Externe Tools|IDG\_VS\_TOOLS\_EXT\_TOOLS|  
|Externe Anpassungen|IDG\_VS\_TOOLS\_EXT\_CUST|  
  
### Fenster Menügruppen  
  
|Gruppieren|ID|  
|----------------|--------|  
|Neu|IDG\_VS\_WINDOW\_NEW|  
|Andocken\/schließen|IDG\_VS\_DOCKCLOSE|  
|Dock ein\-\/ausblenden|IDG\_VS\_DOCKHIDE|  
|Anordnen|IDG\_VS\_WINDOW\_ARRANGE|  
|Navigation|IDG\_VS\_WINDOW\_NAVIGATION|  
|Liste|IDG\_VS\_WINDOW\_LIST|  
  
### Menügruppen\-Hilfe  
  
|Gruppieren|ID|  
|----------------|--------|  
|Proben|IDG\_VS\_HELP\_SAMPLES|  
|Unterstützung|IDG\_VS\_HELP\_SUPPORT|  
|Info|IDG\_VS\_HELP\_ABOUT|  
  
## Untermenüs des Visual Studio\-Menüs  
 Die folgende Hierarchie veranschaulicht die Untermenüs, die mit den Menüs in der Menüleiste von Visual Studio verknüpft sind. Da nur eine Gruppe ein Menü als übergeordnetes Element verfügen kann, muss jede Untermenü aus einer Gruppe in einem Menü statt direkt über das Menü weitergegeben. Weitere Informationen über die Beziehung zwischen Menüs, Gruppen und Untermenüs finden Sie unter [Hinzufügen eines Untermenüs zu einem Menü](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Die Namen der Menüs in der Menüleiste von Visual Studio sind nicht separat angezeigt in dieser Hierarchie, da sie die Benennungskonvention für Gruppen in der IDE wie folgt abgeleitet werden können: IDG\_VS\_*Menünamen*\_*Gruppenname*.  
  
|Übergeordnete Gruppe|Untermenü|Untergeordnete Gruppen|  
|--------------------------|---------------|----------------------------|  
|IDG\_VS\_FILE\_FILE|IDM\_VS\_CSCD\_NEW|IDG\_VS\_FILE\_NEW\_CASCADE|  
||IDM\_VS\_CSCD\_OPEN|IDG\_VS\_FILE\_OPENP\_CASCADE|  
|||IDG\_VS\_FILE\_OPENF\_CASCADE|  
|IDG\_VS\_FILE\_ADD|IDM\_VS\_CSCD\_ADD|IDG\_VS\_FILE\_ADD\_PROJECT\_NEW|  
|||IDG\_VS\_FILE\_ADD\_PROJECT\_EXI|  
|IDG\_VS\_FILE\_MRU|IDM\_VS\_CSCD\_FILEMRU|IDG\_VS\_FILE\_FMRU\_CASCADE|  
||IDM\_VS\_CSCD\_PROJMRU|IDG\_VS\_FILE\_PMRU\_CASCADE|  
|IDG\_VS\_FILE\_MOVE|IDM\_VS\_CSCD\_MOVETOPRJ|IDG\_VS\_FILE\_MOVE\_CASCADE|  
|||IDG\_VS\_FILE\_MOVE\_PICKER|  
|IDG\_VS\_VIEW\_DEV\_WINDOWS|IDM\_VS\_CSCD\_FINDRESULTS|IDG\_VS\_WNDO\_FINDRESULTS|  
||IDM\_VS\_CSCD\_WINDOWS|IDG\_VS\_VIEW\_CALLBROWSER|  
|||IDG\_VS\_WNDO\_OTRWNDWS1... 6|  
|||IDG\_VS\_WNDO\_WINDOWS2|  
|IDG\_VS\_VIEW\_TOOLBARS|IDM\_VS\_CSCD\_COMMANDBARS||  
|IDG\_VS\_EDIT\_GOTO|IDM\_VS\_EDITOR\_FIND\_MENU||  
|IDG\_VS\_EDIT\_OBJECTS|IDM\_VS\_CSCD\_MNUDES|IDG\_VS\_MNUDES\_INSERT|  
|||IDG\_VS\_MNUDES\_EDITNAMES|  
||IDM\_VS\_CSCD\_OLEVERBS|IDG\_VS\_EDIT\_OLEVERBS|  
|IDG\_VS\_BUILD\_SELECTION|IDM\_VS\_CSCD\_BUILD|IDG\_VS\_BUILD\_CASCADE|  
|||IDG\_VS\_BUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_REBUILD|IDG\_VS\_REBUILD\_CASCADE|  
|||IDG\_VS\_REBUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_PROJONLY|IDG\_VS\_PROJONLY\_CASCADE|  
||IDM\_VS\_CSCD\_CLEAN|IDG\_VS\_CLEAN\_CASCADE|  
|||IDG\_VS\_CLEAN\_PROJPICKER|  
||IDM\_VS\_CSCD\_DEPLOY|IDG\_VS\_DEPLOY\_CASCADE|  
|||IDG\_VS\_DEPLOY\_PROJPICKER|  
|IDG\_VS\_PGO\_SELECTION|IDM\_VS\_CSCD\_PGO\_BUILD|IDG\_VS\_PGO\_BUILD\_CASCADE\_BUILD|  
|||IDG\_VS\_PGO\_BUILD\_CASCADE\_RUN|  
  
## Siehe auch  
 [GUIDs und IDs der Visual Studio\-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUIDs und IDs der Visual Studio\-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)