---
title: GUIDs und IDs der Visual Studio-Menüs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 163f7b81295468a69cfb28959f608a21f94a4a99
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134213"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUIDs und IDs der Visual Studio-Menüs
Dieses Thema listet die GUID und ID-Werte, die Menüs und Gruppen in der Visual Studio-Menüleiste. Diese Werte werden in der VSCT-Dateien definiert, die als Teil der Visual Studio-SDK installiert sind. Weitere Informationen finden Sie unter [IDE-Defined Befehle, Menüs und Gruppen](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Weitere Informationen zum Arbeiten mit integrated Development Environment, (IDE) Objekte, die in der VSCT-Dateien definiert sind, finden Sie unter [Erweitern von Menüs und Befehlen](../../extensibility/extending-menus-and-commands.md).  
  
 Verwenden Sie die GUID, die Menüs und Gruppen in der Visual Studio-Menüleiste `guidSHLMainMenu`. Die Menüleiste selbst hat eine ID von `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Gruppen in der Visual Studio-Menüleiste  
 Um ein Menü auf der Menüleiste hinzuzufügen, legen Sie eine dieser Gruppen wie das übergeordnete Objekt.  
  
|Gruppieren|Id|  
|-----------|--------|  
|Datei/Bearbeitungsansicht|IDG_VS_MM_FILEEDITVIEW|  
|Umgestaltung|IDG_VS_MM_REFACTORING:|  
|Projekt|IDG_VS_MM_PROJECT|  
|Build|IDG_VS_MM_BUILDDEBUGRUN|  
|Format-Tools|IDG_VS_MM_TOOLSADDINS|  
|Fenster/Hilfe/Community|IDG_VS_MM_WINDOWHELP|  
|Add-Ins|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Menüs in der Visual Studio-Menüleiste  
 Zum Hinzufügen einer Gruppe zu einem vorhandenen Visual Studio-Menü, legen Sie eine der folgenden Menüs wie das übergeordnete Objekt. Untermenüs sind in dieser Liste nicht enthalten.  
  
|Menü|Id|  
|----------|--------|  
|Datei|IDM_VS_MENU_FILE|  
|Bearbeiten|IDM_VS_MENU_EDIT|  
|Ansicht|IDM_VS_MENU_VIEW|  
|Umgestalten|IDM_VS_MENU_REFACTORING|  
|Projekt|IDM_VS_MENU_PROJECT|  
|Build|IDM_VS_MENU_BUILD|  
|Format|IDM_VS_MENU_FORMAT|  
|Tools|IDM_VS_MENU_TOOLS|  
|Fenster|IDM_VS_MENU_WINDOW|  
|Add-Ins|IDM_VS_MENU_ADDINS|  
|Community|IDM_VS_MENU_COMMUNITY|  
|Hilfe|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Gruppen in Visual Studio-Menüs  
 Die folgenden Listen zeigen, die Gruppen, die direkt von Menüs in der Visual Studio-Menüleiste abgeleitet wird. Die schnellste Möglichkeit zum Hinzufügen eines Befehls zu einem Visual Studio-Menü wird einer dieser Gruppen als übergeordnetes Element festgelegt werden. Gruppen, die von Untermenüs abgeleitet werden in diesem Abschnitt nicht angezeigt.  
  
### <a name="file-menu-groups"></a>Menügruppen Datei  
  
|Gruppieren|Id|  
|-----------|--------|  
|Neue/öffnen|IDG_VS_FILE_FILE|  
|Hinzufügen|IDG_VS_FILE_ADD|  
|Lösung|IDG_VS_FILE_SOLUTION|  
|Sonstiges|IDG_VS_FILE_MISC|  
|Speichern|IDG_VS_FILE_SAVE|  
|Umbenennen|IDG_VS_FILE_RENAME|  
|Browser|IDG_VS_FILE_BROWSER|  
|Print|IDG_VS_FILE_PRINT|  
|Zuletzt verwendet|IDG_VS_FILE_MRU|  
|Verschieben|IDG_VS_FILE_MOVE|  
|Schließen|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Menügruppen bearbeiten  
  
|Gruppieren|Id|  
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
  
|Gruppieren|Id|  
|-----------|--------|  
|Allgemein|IDG_REFACTORING_COMMON|  
|Erweitert|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Menügruppen anzeigen  
  
|Gruppieren|Id|  
|-----------|--------|  
|Formularcode|IDG_VS_VIEW_FORMCODE|  
|Browser|IDG_VS_VIEW_BROWSER|  
|Definieren von Ansichten|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|Architekt Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|Organisation Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|Code-Browser|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Windows dev|IDG_VS_VIEW_DEV_WINDOWS|  
|Symbolleisten|IDG_VS_VIEW_TOOLBARS|  
|Symbole|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Navigieren Sie|IDG_VS_VIEW_NAVIGATE|  
|Kleine navigieren|IDG_VS_VIEW_SMALLNAVIGATE|  
|Objektkatalog|IDG_VS_VIEW_OBJBRWSR|  
|Befehl auch|IDG_VS_VIEW_COMMANDWELL|  
|Eigenschaftenseiten|IDG_VS_VIEW_PROPPAGES|  
|Aktualisieren|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Menügruppen Projekt  
  
|Gruppieren|Id|  
|-----------|--------|  
|Sonstige hinzufügen|IDG_VS_PROJ_MISCADD|  
|Hinzufügen|IDG_VS_PROJ_ADD|  
|Ordner|IDG_VS_PROJ_FOLDER|  
|Laden/Entladen|IDG_VS_PROJ_UNLOADRELOAD|  
|Referenz|IDG_VS_PROJ_REFERENCE|  
|Optionen|IDG_VS_PROJ_OPTIONS|  
|Einstellungen|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Menügruppen erstellen  
  
|Gruppieren|Id|  
|-----------|--------|  
|Lösung|IDG_VS_BUILD_SOLUTION|  
|Auswahl|IDG_VS_BUILD_SELECTION|  
|Profilgesteuerte Optimierung|IDG_VS_PGO_SELECTION|  
|Verschiedenes|IDG_VS_BUILD_MISC|  
|Abbrechen|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Menügruppen Tools  
  
|Gruppieren|Id|  
|-----------|--------|  
|Befehlszeile|IDG_VS_TOOLS_CMDLINE|  
|Codeausschnitte|IDG_VS_TOOLS_SNIPPETS|  
|Objekt-Teilmenge|IDG_VS_TOOLS_OBJSUBSET|  
|Optionen|IDG_VS_TOOLS_OPTIONS|  
|Andere 2|IDG_VS_TOOLS_OTHER2|  
|Externe Tools|IDG_VS_TOOLS_EXT_TOOLS|  
|Externe Anpassungen|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Menügruppen Fenster  
  
|Gruppieren|Id|  
|-----------|--------|  
|Neu|IDG_VS_WINDOW_NEW|  
|Andocken/Close|IDG_VS_DOCKCLOSE|  
|Andocken/ausblenden|IDG_VS_DOCKHIDE|  
|Anordnen|IDG_VS_WINDOW_ARRANGE|  
|Navigation|IDG_VS_WINDOW_NAVIGATION|  
|Liste|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Menügruppen-Hilfe  
  
|Gruppieren|Id|  
|-----------|--------|  
|Proben|IDG_VS_HELP_SAMPLES|  
|Unterstützung|IDG_VS_HELP_SUPPORT|  
|Info|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Untermenüs des Visual Studio-Menüs  
 Die folgende Hierarchie veranschaulicht die Untermenüs, die die Menüs in der Visual Studio-Menüleiste zugeordnet sind. Da nur eine Gruppe ein Menü, wie das übergeordnete Objekt enthalten kann, muss jedem Untermenü aus einer Gruppe in einem Menü statt direkt aus dem Menü weitergegeben. Weitere Informationen über die Beziehung zwischen Menüs, Gruppen und Untermenüs finden Sie unter [ein Menü ein Untermenü hinzugefügt](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Die Namen der Menüs in der Menüleiste von Visual Studio sind nicht separat angezeigt in dieser Hierarchie, da sie die Namenskonvention für Gruppen in der IDE wie folgt abgeleitet werden können: IDG_VS_*Menünamen*_*Gruppenname*.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [GUIDs und IDs der Visual Studio-Symbolleisten](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUIDs und IDs der Visual Studio-Befehle](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)