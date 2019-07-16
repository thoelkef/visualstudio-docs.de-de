---
title: GUIDs und IDs der Visual Studio-Menüs | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26171ae9f4464c3b8b63762d92e9a91d5a4b8420
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329102"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUIDs und IDs von Visual Studio-Menüs
Dieser Artikel listet die GUID und ID-Werte, der die Menüs und Gruppen in der Menüleiste von Visual Studio. Diese Werte werden in definiert *VSCT* Dateien, die als Teil von Visual Studio SDK installiert werden. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Weitere Informationen zum Umgang mit integrated Development Environment (IDE)-Objekten, die definiert sind *VSCT* finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Verwenden Sie die GUID, die Menüs und Gruppen in der Visual Studio-Menüleiste `guidSHLMainMenu`. Die Menüleiste selbst hat eine ID von `IDM_VS_TOOL_MAINMENU`.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppen in der Visual Studio-Menüleiste
 Um ein Menü auf der Menüleiste hinzuzufügen, legen Sie eine dieser Gruppen als übergeordnetes aus.

|Gruppieren|ID|
|-----------|--------|
|Datei/Bearbeiten/Ansicht|IDG_VS_MM_FILEEDITVIEW|
|Umgestaltung|IDG_VS_MM_REFACTORING:|
|Projekt|IDG_VS_MM_PROJECT|
|Build|IDG_VS_MM_BUILDDEBUGRUN|
|Format/Tools|IDG_VS_MM_TOOLSADDINS|
|Fenster/Hilfe/Community|IDG_VS_MM_WINDOWHELP|
|Add-Ins|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menüs in der Visual Studio-Menüleiste
 Um eine Gruppe zu einem vorhandenen Visual Studio-Menü hinzuzufügen, legen Sie eine der die folgenden Menüs als übergeordnete Klasse aus. Untermenüs werden in dieser Liste nicht enthalten.

|Menü|ID|
|----------|--------|
|Datei|IDM_VS_MENU_FILE|
|Bearbeiten|IDM_VS_MENU_EDIT|
|Ansicht|IDM_VS_MENU_VIEW|
|Umgestalten|IDM_VS_MENU_REFACTORING|
|Projekt|IDM_VS_MENU_PROJECT|
|Build|IDM_VS_MENU_BUILD|
|Format|IDM_VS_MENU_FORMAT|
|Tools|IDM_VS_MENU_TOOLS|
|Erweiterungen|IDM_VS_MENU_EXTENSIONS|
|Fenster|IDM_VS_MENU_WINDOW|
|Add-Ins|IDM_VS_MENU_ADDINS|
|Community|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Gruppen in Visual Studio-Menüs
 Im folgenden wird aufgeführt, der Gruppen, die direkt von Menüs in der Visual Studio-Menüleiste abgeleitet. Die schnellste Möglichkeit zum Hinzufügen eines Befehls zu einem Visual Studio-Menü ist einer dieser Gruppen als übergeordnetes Element festlegen. Gruppen, die von Untermenüs abgeleitet werden in diesem Abschnitt nicht angezeigt.

### <a name="file-menu-groups"></a>Dateigruppen-Menü

|Gruppieren|ID|
|-----------|--------|
|Neue/öffnen|IDG_VS_FILE_FILE|
|Hinzufügen|IDG_VS_FILE_ADD|
|Lösung|IDG_VS_FILE_SOLUTION|
|Sonstiges|IDG_VS_FILE_MISC|
|Speichern|IDG_VS_FILE_SAVE|
|Umbenennen|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Print|IDG_VS_FILE_PRINT|
|Die zuletzt verwendet|IDG_VS_FILE_MRU|
|Verschieben|IDG_VS_FILE_MOVE|
|Schließen|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Menügruppen bearbeiten

|Gruppieren|ID|
|-----------|--------|
|Rückgängig/Wiederholen|IDG_VS_EDIT_UNDOREDO|
|Ausschneiden/Kopieren/Einfügen|IDG_VS_EDIT_CUTCOPY|
|Auswählen|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|erzwingen|IDG_VS_EDIT_OBJECTS|
|OLE-Verben|IDG_VS_EDIT_OLEVERBS|
|Befehl auch|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Menügruppen Umgestalten

|Gruppieren|ID|
|-----------|--------|
|Allgemeine|IDG_REFACTORING_COMMON|
|Erweitert|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Menügruppen anzeigen

|Gruppieren|ID|
|-----------|--------|
|Form-Code|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Ansichten definieren|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Entwerfen von Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Organisation Windows|IDG_VS_VIEW_ORG_WINDOWS|
|Code-Browser|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Dev Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Symbolleisten|IDG_VS_VIEW_TOOLBARS|
|Symbole|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navigate|IDG_VS_VIEW_NAVIGATE|
|Navigieren Sie kleine.|IDG_VS_VIEW_SMALLNAVIGATE|
|Objektkatalog|IDG_VS_VIEW_OBJBRWSR|
|Befehl auch|IDG_VS_VIEW_COMMANDWELL|
|Eigenschaftenseiten|IDG_VS_VIEW_PROPPAGES|
|Aktualisieren|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Projektgruppen-Menü

|Gruppieren|ID|
|-----------|--------|
|Sonstige hinzufügen|IDG_VS_PROJ_MISCADD|
|Hinzufügen|IDG_VS_PROJ_ADD|
|Ordner|IDG_VS_PROJ_FOLDER|
|Entladen/Aufladen|IDG_VS_PROJ_UNLOADRELOAD|
|Referenz|IDG_VS_PROJ_REFERENCE|
|Optionen|IDG_VS_PROJ_OPTIONS|
|Einstellungen|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Menügruppen erstellen

|Gruppieren|ID|
|-----------|--------|
|Lösung|IDG_VS_BUILD_SOLUTION|
|Auswahl|IDG_VS_BUILD_SELECTION|
|Profilgesteuerte Optimierung|IDG_VS_PGO_SELECTION|
|Verschiedenes|IDG_VS_BUILD_MISC|
|Abbrechen|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Menügruppen Tools

|Gruppieren|ID|
|-----------|--------|
|Befehlszeile|IDG_VS_TOOLS_CMDLINE|
|Codeausschnitte|IDG_VS_TOOLS_SNIPPETS|
|Objekt-Teilmenge|IDG_VS_TOOLS_OBJSUBSET|
|Optionen|IDG_VS_TOOLS_OPTIONS|
|Andere 2|IDG_VS_TOOLS_OTHER2|
|Externe Tools|IDG_VS_TOOLS_EXT_TOOLS|
|Externe Anpassungen|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Menügruppen Fenster

|Gruppieren|ID|
|-----------|--------|
|Neu|IDG_VS_WINDOW_NEW|
|Andocken/geschlossen|IDG_VS_DOCKCLOSE|
|Andocken/ausblenden|IDG_VS_DOCKHIDE|
|Anordnen|IDG_VS_WINDOW_ARRANGE|
|Navigation|IDG_VS_WINDOW_NAVIGATION|
|Liste|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Menügruppen-Hilfe

|Gruppieren|ID|
|-----------|--------|
|Proben|IDG_VS_HELP_SAMPLES|
|Unterstützung|IDG_VS_HELP_SUPPORT|
|Info|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Untermenüs des Visual Studio-Menüs
 Die folgende Hierarchie veranschaulicht die Untermenüs, die die Menüs auf der Menüleiste von Visual Studio zugeordnet sind. Da nur eine Gruppe ein Menüs als das übergeordnete Element verfügen kann, muss jedem Untermenü aus einer Gruppe in einem Menü, anstatt direkt über das Menü abgeleitet werden. Weitere Informationen über die Beziehung zwischen Menüs, Untermenüs und Gruppen finden Sie unter [Hinzufügen eines Untermenüs zu einem Menü](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Die Namen der Menüs in der Menüleiste von Visual Studio werden nicht separat in dieser Hierarchie angezeigt, da sie wie folgt von der Namenskonvention für Gruppen in der IDE abgeleitet werden können: *IDG_VS_\<Menünamen\>_\<Gruppenname\>* .

|Übergeordnete Gruppe|Untermenü|Untergeordnete Gruppen|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1...6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>Siehe auch
- [GUIDs und IDs von Visual Studio-Symbolleiste](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUIDs und IDs von Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
