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
ms.openlocfilehash: c4ffef0b1b76f453048ff20e3cbada0b8a591c65
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388831"
---
# <a name="options-text-editor-cc-view"></a>Optionen, Text-Editor, C/C++, Ansicht

Verwenden Sie diesen Eigenschaftenseiten, um das Standardverhalten des Code-Editors zu ändern, wenn Sie in C oder C++ programmieren.

Wählen Sie **Tools** > **Optionen** aus, erweitern Sie **Text-Editor** und dann **C/C++**, und wählen Sie **Ansicht** aus, um auf diese Eigenschaftenseite zuzugreifen.

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
