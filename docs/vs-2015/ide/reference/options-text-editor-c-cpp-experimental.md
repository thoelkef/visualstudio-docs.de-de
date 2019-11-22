---
title: Optionen, Text-Editor, C/C++, Experimentell | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5979363f16f2e9d78a2f50ffbb6511d03146caaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297851"
---
# <a name="options-text-editor-cc-experimental"></a>Optionen, Text-Editor, C/C++, Experimentell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie diese Optionen ändern, können Sie beim Programmieren in C oder C++ das Verhalten ändern, das mit IntelliSense und der Suchdatenbank zusammenhängt.

 Um auf diese Seite zuzugreifen, erweitern Sie im Dialogfeld **Optionen** im linken Bereich den Eintrag **Text-Editor**, erweitern Sie **C/C++** , und wählen Sie dann **Experimental**aus.

 Diese Features sind in einer Visual Studio 2015 Update 1 RC-Installation verfügbar.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Informationen hierzu finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio)](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Durchsuchen/Navigation
 **Enable New Database Engine** This should automatically speed up database population and make all database operations faster (with no loss in accuracy) for operations such as **Go To Definition** and **Find All References**. (Sie müssen Ihre Projektmappe nur schließen und erneut öffnen , um die Änderungen anzuwenden. Es ist nicht erforderlich, Visual Studio neu zu starten.)

## <a name="intellisense"></a>IntelliSense
 **Member List Dot-To-Arrow** Replaces '.' with '->' when applicable for Member List.

## <a name="refactoring"></a>Umgestaltung
 **Enable Extract Function** Extract selected code to its own function and replace code with a call to the new function. Um auf dieses Feature zuzugreifen, klicken Sie mit der rechten Maustaste auf den ausgewählten Code, und wählen Sie **Schnelle Aktionen**aus, oder drücken Sie einfach die Standardtastenkombination STRG + Punkt [STRG + .].

 **Enable Change Signature** Add, reorder, and delete parameters of a function and propagate the changes to all call sites. Um auf dieses Feature zuzugreifen, klicken Sie mit der rechten Maustaste auf irgendeinen Aufruf der Funktion, und wählen Sie **Schnelle Aktionen**aus, oder drücken Sie einfach die Standardtastenkombination STRG + Punkt [STRG + .].

## <a name="text-editor"></a>Text-Editor
 **Enable Expand Scopes** If enabled, you can surround selected text with curly braces by typing '{' into the text editor.

 **Enable Expand Precedence** If enabled, you can surround selected text with parentheses by typing '(' into the text editor.

 Weitere Text-Editor-Features für die Visual Studio Gallery finden Sie in der Liste [hier](https://go.microsoft.com/fwlink/?LinkId=692016). Ein Beispiel ist [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), das Folgendes unterstützt:

- **Add missing #include** - Schlägt zutreffende #include-Anweisungen für unbekannte Symbole in Ihrem Code vor.

- **Add using namespace/Fully qualify symbol** - Wie die vorherige Option, aber für Namespaces.

- **Add missing semicolon**

- **MSDN Help** - In MSDN nach Fehlermeldungen suchen.

  Sie können entweder mit dem Mauszeiger auf eine Wellenlinie zeigen, um eine Glühbirne anzuzeigen, oder die Standardtastenkombination Strg + Punkt (STRG + .) verwenden. Für die Tastenkombination muss die Einfügemarke nicht auf dem speziellen Fehler oder Token positioniert werden. Es genügt, wenn Sie sich in der Zeile befinden, in der der Fehler auftritt, um Vorschläge für alle Elemente in dieser Zeile aufzurufen.

## <a name="see-also"></a>Siehe auch
 [Setting Language-Specific Editor Options](../../ide/reference/setting-language-specific-editor-options.md) [Refactoring in C++ (VC Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
