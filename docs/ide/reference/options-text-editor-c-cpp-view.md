---
title: Optionen, Text-Editor, C/C++, Ansicht
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf1cde04a45df47627b8b8bf9a0fad7b9bef0c4
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673236"
---
# <a name="options-text-editor-cc-view"></a>Optionen, Text-Editor, C/C++, Ansicht

Verwenden Sie diesen Eigenschaftenseiten, um das Standardverhalten des Code-Editors zu ändern, wenn Sie in C oder C++ programmieren.

Wählen Sie **Tools** > **Optionen** aus, erweitern Sie **Text-Editor** und dann **C/C++**, und wählen Sie **Ansicht** aus, um auf diese Eigenschaftenseite zuzugreifen.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="code-squiggles"></a>Wellenlinien im Code

Sie können die folgenden Einstellungen aktivieren oder deaktivieren, um festzulegen, wie der Text-Editor Wellenlinien im Code für C und C++ behandelt:

- **Macros in Skipped Browsing Regions** (Makros in übersprungenen Suchbereichen): Definiert, wie Makros hervorgehoben werden, die sich in von der Suchdatenbank übersprungenen Bereichen befinden, darunter Makros, deren Definitionen geschweifte Klammern beinhalten.

- **Macros Convertible to constexpr** (Makros können in constexpr konvertiert werden): Definiert, wie Makrodefinitionen hervorgehoben werden, die in `constexpr`-Definitionen konvertiert werden können.

## <a name="inactive-code"></a>Inaktiver Code

- **Inaktive Blocks anzeigen:** Inaktive Präprozessorblocks werden unterschiedlich eingefärbt.

- **Durchlässigkeit inaktiven Codes deaktivieren:** Anstelle der Durchlässigkeit für inaktive Codeblocks wird eine Volltonfarbe verwendet.

- **Durchlässigkeitsprozentsatz inaktiven Codes:** Der Durchlässigkeitsprozentsatz inaktiver Codeblocks.

## <a name="miscellaneous"></a>Verschiedenes

- **Kommentaraufgaben aufzählen:** Quelldateien auf VS-Token prüfen und Vorkommnisse im Aufgabenlistenfenster aufführen.

- **Übereinstimmende Token hervorheben:** Einschließende Klammern oder Syntax werden hervorgehoben, wenn der Cursor über ein übereinstimmendes Element bewegt wird. 

## <a name="outlining"></a>Gliedern

- **Gliederung aktivieren:** Startet den Gliederungsmodus beim Öffnen einer Datei.

- **Pragmabereiche gliedern:** Automatische Gliederung von `#pragma`-Bereichblocks.

- **Anweisungsblocks gliedern:** Automatische Gliederung von Anweisungsblocks.

## <a name="see-also"></a>Siehe auch

- [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)
- [Umgestaltung in C++ (VC-Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
