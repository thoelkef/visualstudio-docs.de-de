---
title: Verwalten externer Tools | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.externaltools
helpviewer_keywords: external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3e796b1e5a1773183c04409781cf6e2026bfe96e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="manage-external-tools"></a>Verwalten externer Tools

Sie können externe Tools aus Visual Studio mithilfe des **Extras**-Menüs aufrufen. Einige Standardtools sind im Menü **Extras** verfügbar. Sie können das Menü jedoch auch anpassen, indem Sie andere ausführbare Dateien (eigene Dateien) hinzufügen.

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Im Menü „Extras“ von Visual Studio verfügbare Tools

Das Menü **Extras** enthält mehrere integrierte Befehle, z.B.:

* **Erweiterungen und Updates** für die [Verwaltung von Visual Studio-Erweiterungen](finding-and-using-visual-studio-extensions.md)
* **Codeausschnitt-Manager...** zum [Organisieren von Codeausschnitten](code-snippets.md#code-snippet-manager)
* **PreEmptive-Schutz: Dotfuscator** zum Starten von [Dotfuscator Community Edition (CE)](dotfuscator/index.md), sofern [installiert](dotfuscator/install.md).
* **Anpassen...** zum [Anpassen von Menüs und Symbolleisten](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Optionen...** zum [Festlegen einer Vielzahl verschiedener Optionen für die Visual Studio-IDE und andere Tools](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Neue Tools zum Menü „Extras“ hinzufügen

Sie können ein externes Tool hinzufügen, das im Menü **Extras** angezeigt wird.

1. Öffnen Sie das Dialogfeld **Externe Tools**, indem Sie **Extras** > **Externe Tools...**  auswählen.

1. Klicken Sie auf **Hinzufügen**, und geben Sie dann die Informationen ein. Beispielsweise führt der folgende Eintrag dazu, dass Windows Explorer in dem Verzeichnis der Datei geöffnet wird, das Sie zurzeit in Visual Studio geöffnet haben:

   * Titel: `Open File Location`

   * Befehl: `explorer.exe`

   * Argumente: `/root, "$(ItemDir)"`

   ![Dialogfeld „Externe Tools“](media/external-tools-dialog.png)

Im Folgenden finden Sie eine Liste der Argumente, die verwendet werden können, wenn Sie ein externes Tool definieren:

|name|Argument|description|  
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
|Binäres Verzeichnis|$(BinDir)|Der endgültige Position der Binärdatei, die erstellt wird (als Laufwerk + Pfad definiert).|  
|Projektverzeichnis|$(ProjDir)|Das Verzeichnisses des aktuellen Projekts (Laufwerk + Pfad).|  
|Projektdateiname|$(ProjFileName)|Der Dateiname des aktuellen Projekts (Laufwerk + Pfad + Dateiname).|  
|Projektmappenverzeichnis|$(SolutionDir)|Das Verzeichnisses der aktuellen Projektmappe (Laufwerk + Pfad).|  
|Projektmappen-Dateiname|$(SolutionFileName)|Der Dateiname der aktuellen Projektmappe (Laufwerk + Pfad + Dateiname).|

> [!NOTE]
> In der IDE-Statusleiste werden die Variablen "Aktuelle Zeile" und "Aktuelle Spalte" angezeigt, um die Position der Einfügemarke im aktiven Code-Editor anzuzeigen. Die Variable "Aktueller Text" gibt den an dieser Stelle ausgewählten Text oder Code zurück.

## <a name="see-also"></a>Siehe auch

[C/C++-Buildtools](/cpp/build/reference/c-cpp-build-tools)
