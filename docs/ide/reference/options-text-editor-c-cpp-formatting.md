---
title: Optionen, Text-Editor, C/C++, Formatierung
ms.date: 04/30/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa4c543d19c43bd397d7d18a185a73a4bf161a6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960747"
---
# <a name="options-text-editor-cc-formatting"></a>Optionen, Text-Editor, C/C++, Formatierung

Verwenden Sie diesen Eigenschaftenseiten, um das Standardverhalten des Code-Editors zu ändern, wenn Sie in C oder C++ programmieren.

[Eigenschaftenseiten für die C++-Formatierung](media/cpp-formatting.png)

 Um diese Seite zu öffnen, klicken Sie im linken Fenster auf das Dialogfeld **Optionen**, erweitern Sie den **Text-Editor** und **C/C++** und klicken dann auf **Formatieren**.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Seite "Allgemein"

Diese Seite enthält Optionen für das Formatieren von Anweisungen und Blöcken während der Eingabe.

**Visual Studio 2017 Version 15.7 und höher**: Die Seite enthält ferner Optionen für das Konfigurieren der Unterstützung für [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) Version 5.0. ClangFormat ist ein Hilfsprogramm, den Stil und die Formatierung Ihres Codes einfach basierend auf Regeln anpassen können, die in einer Datei mit der Erweiterung „.clang-format“ oder „_clang-format“ konfiguriert werden können.

### <a name="configuring-clangformat-options"></a>Konfigurieren von ClangFormat-Optionen

In Visual Studio 2017 (Version 15.7 und höher) ist die ClangFormat-Unterstützung standardmäßig aktiviert. Sie können auswählen, welcher dieser gängigen Formatierungskonventionen auf Ihre Projekte angewendet werden sollen: LLVM, Google, Chromium, Mozilla oder WebKit. Sie können ebenfalls eine benutzerdefinierte Datei („.clang-format“ oder „_clang-format“) für die Definition des Formats erstellen. Wenn eine solche Datei in einem Projektordner vorhanden ist, verwendet Visual Studio diese, um alle Quellcodedateien in diesem Ordner und dessen Unterordnern zu formatieren. 

Standardmäßig führt Visual Studio „clangformat.exe“ im Hintergrund aus, wodurch die Formatierung während der Eingabe angewendet wird. Sie können ebenfalls festlegen, dass die Datei nur für manuell aufgerufene Formatierungsfehle wie **Dokument formatieren (STRG+K, STRG+D)** oder **Auswahl formatieren (STRG+K, STRG+F)** ausgeführt wird.


## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Seiten „Einzug“, „Neue Zeilen“, „Abstand“, „Umbruch“

Diese Seiten ermöglichen verschiedene Anpassungen der Formatierung, werden jedoch ignoriert, wenn ClangFormat aktiviert ist.

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
- [Verwenden von IntelliSense](../../ide/using-intellisense.md)