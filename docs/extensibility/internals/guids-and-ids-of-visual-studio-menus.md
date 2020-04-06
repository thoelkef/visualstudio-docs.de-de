---
title: GUIDs und IDs von Visual Studio-Menüs | Microsoft Docs
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a656d5cb9a126a9dc3988d70a290fceb3e56439e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708242"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUIDs und IDs von Visual Studio-Menüs
In diesem Artikel werden die GUID- und ID-Werte der Menüs und Gruppen in der Visual Studio-Menüleiste aufgezählt. Diese Werte werden in *.vsct-Dateien* definiert, die als Teil des Visual Studio SDK installiert werden. Weitere Informationen finden Sie unter [IDE-definierte Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Weitere Informationen zum Arbeiten mit IDE-Objekten (Integrated Development Environment) finden Sie *unter* Erweitern von [Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).

 Die Menüs und Gruppen in der Visual `guidSHLMainMenu`Studio-Menüleiste verwenden die GUID . Die Menüleiste selbst hat `IDM_VS_TOOL_MAINMENU`die ID von .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppen in der Visual Studio-Menüleiste
 Um der Menüleiste ein Menü hinzuzufügen, legen Sie eine dieser Gruppen als übergeordnete Gruppe fest.

|Group|id|
|-----------|--------|
|Datei/Bearbeiten/Anzeigen|IDG_VS_MM_FILEEDITVIEW|
|Refactoring|IDG_VS_MM_REFACTORING:|
|Project|IDG_VS_MM_PROJECT|
|Build|IDG_VS_MM_BUILDDEBUGRUN|
|Format/Tools|IDG_VS_MM_TOOLSADDINS|
|Fenster/Hilfe/Community|IDG_VS_MM_WINDOWHELP|
|Add-Ins|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menüs in der Visual Studio-Menüleiste
 Um eine Gruppe zu einem vorhandenen Visual Studio-Menü hinzuzufügen, legen Sie eines der folgenden Menüs als übergeordnetes Menü fest. Untermenüs sind in dieser Liste nicht enthalten.

|Menü|id|
|----------|--------|
|Datei|IDM_VS_MENU_FILE|
|Edit (Bearbeiten)|IDM_VS_MENU_EDIT|
|Ansicht|IDM_VS_MENU_VIEW|
|Refactoring|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Build|IDM_VS_MENU_BUILD|
|Format|IDM_VS_MENU_FORMAT|
|Tools|IDM_VS_MENU_TOOLS|
|Erweiterungen|IDM_VS_MENU_EXTENSIONS|
|Fenster|IDM_VS_MENU_WINDOW|
|Add-Ins|IDM_VS_MENU_ADDINS|
|Community|IDM_VS_MENU_COMMUNITY|
|Hilfe|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Gruppen in Visual Studio-Menüs
 Die folgenden Listen zeigen die Gruppen, die direkt von menüs in der Visual Studio-Menüleiste abstammen. Die schnellste Möglichkeit, einem Visual Studio-Menü einen Befehl hinzuzufügen, besteht darin, eine dieser Gruppen als übergeordnete Gruppe festzulegen. Gruppen, die aus Untermenüs abstammen, werden in diesem Abschnitt nicht angezeigt.

### <a name="file-menu-groups"></a>Dateimenügruppen

|Group|id|
|-----------|--------|
|Neu/Offen|IDG_VS_FILE_FILE|
|Hinzufügen|IDG_VS_FILE_ADD|
|Lösung|IDG_VS_FILE_SOLUTION|
|Sonstiges|IDG_VS_FILE_MISC|
|Speichern|IDG_VS_FILE_SAVE|
|Umbenennen|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|print|IDG_VS_FILE_PRINT|
|Zuletzt verwendet|IDG_VS_FILE_MRU|
|Move|IDG_VS_FILE_MOVE|
|Beenden|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Menügruppen bearbeiten

|Group|id|
|-----------|--------|
|Rückgängig/Wiederholen|IDG_VS_EDIT_UNDOREDO|
|Ausschneiden/Kopieren/Einfügen|IDG_VS_EDIT_CUTCOPY|
|Select|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Suchen|IDG_VS_EDIT_FIND|
|erzwingen|IDG_VS_EDIT_OBJECTS|
|OLE Verben|IDG_VS_EDIT_OLEVERBS|
|Command Well|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Umgestalten von Menügruppen

|Group|id|
|-----------|--------|
|Allgemein|IDG_REFACTORING_COMMON|
|Erweitert|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Menügruppen anzeigen

|Group|id|
|-----------|--------|
|Formularcode|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Definieren von Ansichten|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Architekt Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Organisation Windows|IDG_VS_VIEW_ORG_WINDOWS|
|Code-Browser|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Dev Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Symbolleisten|IDG_VS_VIEW_TOOLBARS|
|Symbols|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Navigieren|IDG_VS_VIEW_NAVIGATE|
|Kleine Navigation|IDG_VS_VIEW_SMALLNAVIGATE|
|Objektkatalog|IDG_VS_VIEW_OBJBRWSR|
|Command Well|IDG_VS_VIEW_COMMANDWELL|
|Eigenschaftenseiten|IDG_VS_VIEW_PROPPAGES|
|Aktualisieren|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Projektmenügruppen

|Group|id|
|-----------|--------|
|Verschiedenes hinzufügen|IDG_VS_PROJ_MISCADD|
|Hinzufügen|IDG_VS_PROJ_ADD|
|Ordner|IDG_VS_PROJ_FOLDER|
|Entladen/Nachladen|IDG_VS_PROJ_UNLOADRELOAD|
|Referenz|IDG_VS_PROJ_REFERENCE|
|Optionen|IDG_VS_PROJ_OPTIONS|
|Einstellungen|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Erstellen von Menügruppen

|Group|id|
|-----------|--------|
|Lösung|IDG_VS_BUILD_SOLUTION|
|Auswahl|IDG_VS_BUILD_SELECTION|
|Profilgesteuerte Optimierung|IDG_VS_PGO_SELECTION|
|Verschiedenes|IDG_VS_BUILD_MISC|
|Abbrechen|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Werkzeuge Menügruppen

|Group|id|
|-----------|--------|
|Befehlszeile|IDG_VS_TOOLS_CMDLINE|
|Codeausschnitte|IDG_VS_TOOLS_SNIPPETS|
|Objektuntermenge|IDG_VS_TOOLS_OBJSUBSET|
|Optionen|IDG_VS_TOOLS_OPTIONS|
|Sonstiges 2|IDG_VS_TOOLS_OTHER2|
|Externe Tools|IDG_VS_TOOLS_EXT_TOOLS|
|Externe Anpassungen|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Fenstermenügruppen

|Group|id|
|-----------|--------|
|Neu|IDG_VS_WINDOW_NEW|
|Dock/Schließen|IDG_VS_DOCKCLOSE|
|Dock/Hide|IDG_VS_DOCKHIDE|
|Anordnen|IDG_VS_WINDOW_ARRANGE|
|Navigation|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Hilfemenügruppen

|Group|id|
|-----------|--------|
|Beispiele|IDG_VS_HELP_SAMPLES|
|Support|IDG_VS_HELP_SUPPORT|
|Info|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Untermenüs von Visual Studio-Menüs
 Die folgende Hierarchie zeigt die Untermenüs, die den Menüs in der Visual Studio-Menüleiste zugeordnet sind. Da nur eine Gruppe ein Menü als übergeordnetes Menü haben kann, muss jedes Untermenü von einer Gruppe in einem Menü abstammen und nicht direkt aus dem Menü. Weitere Informationen zur Beziehung zwischen Menüs, Gruppen und Untermenüs finden Sie unter [Hinzufügen eines Untermenüs zu einem Menü](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Die Namen der Menüs in der Visual Studio-Menüleiste werden in dieser Hierarchie nicht separat angezeigt, da sie aus der Namenskonvention für Gruppen in der IDE wie folgt abgeleitet werden können: *IDG_VS_\<Menüname\>_\<Gruppenname\>*.

|Übergeordnete Gruppe|Untermenü|Kindergruppen|
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
|||IDG_VS_WNDO_OTRWNDWS1... 6|
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

## <a name="see-also"></a>Weitere Informationen
- [GUIDs und IDs von Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUIDs und IDs von Visual Studio-Befehlen](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio-Befehlstabellendateien (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
