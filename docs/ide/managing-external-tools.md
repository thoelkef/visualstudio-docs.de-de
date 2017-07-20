---
title: Verwalten externer Tools | Microsoft-Dokumentation
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- Create GUID tool
- RC (Resource Compiler)
- ReBase tool
- Windows NT Message Compiler
- Windows NT C++ Symbol Undecorator
- tstcon32.exe
- Type Library Generator
- Windows NT Image Binder
- tools [Visual Studio], external
- RowsetViewer tool
- utilities, external tools
- Local Test Manager
- OLE DB Rowset Viewer
- Midlc (IDL Compiler)
- ATL Trace Tool
- Odbcte32w.exe
- IDL Compiler
- HCW (Help Workshop)
- Message Compiler [Visual Studio]
- UUID Generator
- MIDL, external tools
- ErrLook tool
- MAKEHM tool
- Error lookup tool
- OLEVIEW (Object Viewer)
- Uuidgen.exe
- WebDbg tool
- OLE/COM Object Viewer
- LTM (Local Test Manager)
- ATLTraceTool.exe
- Bind tool
- Vsvars32.bat
- external tools [Visual Studio]
- ODBC Test
- Windows NT Image Rebaser
- undname.exe
- Vcspawn.exe
- ActiveX Control Test Container
- mc (Message Compiler)
- GUIDGEN tool
- Odbcte32.exe
- DisableMsg tool
- MkTypLib tool
- Help Workshop
- Resource Compiler
ms.assetid: f382fd40-a98f-4934-8c9a-5aeae881acde
caps.latest.revision: 38
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 1d273749cc41eb975dc9f93329edf9a57aaae09a
ms.contentlocale: de-de
ms.lasthandoff: 05/24/2017

---
# Verwalten externer Tools
<a id="manage-external-tools" class="xliff"></a>
Sie können externe Tools aus Visual Studio mithilfe des **Extras**-Menüs aufrufen. Einige Standardtools sind im Menü **Extras** verfügbar, Sie können jedoch andere eigene ausführbare Dateien hinzufügen.  

## Im Menü „Extras“ von Visual Studio verfügbare Tools
<a id="tools-available-on-the-visual-studio-tools-menu" class="xliff"></a>
 Das Menü **Extras** enthält mehrere integrierte Befehle, z.B.:

*  **Erweiterungen und Updates** für die [Verwaltung von Visual Studio-Erweiterungen](finding-and-using-visual-studio-extensions.md)
*  **Codeausschnitt-Manager...** zum [Organisieren von Codeausschnitten](code-snippets.md#code-snippet-manager)
*  **PreEmptive-Schutz: Dotfuscator** zum Starten von [Dotfuscator Community Edition (CE)](dotfuscator/index.md), sofern [installiert](dotfuscator/install.md).
*  **Anpassen...** zum [Anpassen von Menüs und Symbolleisten](how-to-customize-menus-and-toolbars-in-visual-studio.md)
*  **Optionen...** zum [Festlegen einer Vielzahl verschiedener Optionen für die Visual Studio-IDE und andere Tools](reference/options-dialog-box-visual-studio.md)

## Neue Tools zum Menü „Extras“ hinzufügen
<a id="add-new-tools-to-the-tools-menu" class="xliff"></a> 
 So können im Menü **Extras** ein externes Tool hinzufügen. Öffnen Sie das Dialogfeld **Externe Tools...**, und klicken Sie auf **Hinzufügen**. Geben Sie dann die Informationen ein. Beispielsweise führt der folgende Eintrag dazu, dass Windows Explorer in dem Verzeichnis der Datei geöffnet wird, das Sie zurzeit in Visual Studio geöffnet haben:  
  
1.  Titel: *Dateispeicherort öffnen*
  
2.  Befehl: `explorer.exe`  
  
3.  Argumente: `/root, "$(ItemDir)"`  
  
 Im Folgenden finden Sie eine Liste der Argumente, die verwendet werden können, wenn Sie ein externes Tool definieren.
  
> [!NOTE]
>  In der IDE-Statusleiste werden die Variablen "Aktuelle Zeile" und "Aktuelle Spalte" angezeigt, um die Position der Einfügemarke im aktiven Code-Editor anzuzeigen. Die Variable "Aktueller Text" gibt den an dieser Stelle ausgewählten Text oder Code zurück.  
  
|Name|Argument|Beschreibung|  
|----------|--------------|-----------------|  
|Elementpfad|$(ItemPath)|Der vollständige Dateiname der aktuellen Datei (Laufwerk + Pfad + Dateiname).|  
|Elementverzeichnis|$(ItemDir)|Das Verzeichnisses der aktuellen Datei (Laufwerk + Pfad).|  
|Elementdateiname|$(ItemFilename)|Der Dateiname der aktuellen Datei (Dateiname).|  
|Elementerweiterung|$(ItemExt)|Die Dateinamenerweiterung der aktuellen Datei.|  
|Aktuelle Zeile|&(CurLine)|Die aktuelle Zeilenposition des Cursors im Codefenster.|  
|Aktuelle Spalte|&(CurCol)|Die aktuelle Spaltenposition des Cursors im Codefenster.|  
|Aktueller Text|&(CurText)|Der ausgewählte Text.|  
|Zielpfad|$(TargetPath)|Der vollständige Dateiname des zu erstellenden Elements (Laufwerk + Pfad + Dateiname).|  
|Target Directory|$(TargetDir)|Das Verzeichnis des zu erstellenden Elements.|  
|Target Name|$(TargetName)|Der Dateiname des zu erstellenden Elements.|  
|Zielerweiterung|$(TargetExt)|Die Dateinamenerweiterung zu erstellenden Elements.|  
|Binäres Verzeichnis|$(BinDir)|Der endgültige Position der Binärdatei, die erstellt wird (als Laufwerk + Pfad definiert). Beispiel: **\\...\Eigene Dateien\ Visual Studio-\<Version >\\<ProjectName\>\bin\debug**|  
|Projektverzeichnis|$(ProjDir)|Das Verzeichnisses des aktuellen Projekts (Laufwerk + Pfad).|  
|Projektdateiname|$(ProjFileName)|Der Dateiname des aktuellen Projekts (Laufwerk + Pfad + Dateiname).|  
|Projektmappenverzeichnis|$(SolutionDir)|Das Verzeichnisses der aktuellen Projektmappe (Laufwerk + Pfad).|  
|Projektmappen-Dateiname|$(SolutionFileName)|Der Dateiname der aktuellen Projektmappe (Laufwerk + Pfad + Dateiname).|  

## Siehe auch
<a id="see-also" class="xliff"></a>  
 [C/C++-Buildtools](/cpp/build/reference/c-cpp-build-tools)

