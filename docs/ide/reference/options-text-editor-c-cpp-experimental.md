---
title: Optionen, Text-Editor, C/C++, Experimentell
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 088359aeabc45966aed927693ecbab75751eca2a
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58789990"
---
# <a name="options-text-editor-cc-experimental"></a>Optionen, Text-Editor, C/C++, Experimentell

Wenn Sie diese Optionen ändern, können Sie beim Programmieren in C oder C++ das Verhalten ändern, das mit IntelliSense und der Suchdatenbank zusammenhängt. Diese Features sind rein experimentell und werden möglicherweise in einem zukünftigen Release geändert oder komplett aus Visual Studio entfernt.

::: moniker range="vs-2017"

In diesem Artikel werden die Optionen in Visual Studio 2017 beschrieben. Wenn Sie Visual Studio 2015 verwenden, wählen Sie in der Auswahl oberhalb des Inhaltsverzeichnisses **2015** aus.

::: moniker-end

Drücken Sie **STRG**+**Q**, um das Suchfeld zu aktivieren, und geben Sie anschließend **experimentell** ein, um auf diese Eigenschaftenseite zuzugreifen. Die Suche findet die Seite nach den ersten Buchstaben. Sie können auch darauf zugreifen, indem Sie **Tool** > **Optionen** auswählen, den **Text-Editor** und **C/C++** erweitern und anschließend **Experimentell** auswählen.

Diese Features sind mit einer Visual Studio-Installation verfügbar.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Aktivieren von Predictive IntelliSense

Predictive IntelliSense beschränkt die Anzahl von angezeigten Ergebnissen in der Dropdownliste in IntelliSense, sodass nur für Ihren Kontext relevante Ergebnisse angezeigt werden. Wenn Sie z.B. `int x =` eingeben und das Dropdownmenü in IntelliSense aufrufen, werden Ihnen nur Integer oder Funktionen angezeigt, die Integer zurückgeben. Standardmäßig ist Predictive IntelliSense deaktiviert.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Aktivieren von „Schnelleres Laden von Projekten“

Ab Visual Studio 2017, Version 15.3 und höher heißt diese Funktion **Enable Project Caching** (Zwischenspeichern des Projekts aktivieren) und wurde auf die Eigenschaftenseite [VC++-Projekteinstellungen](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) verschoben.

Durch diese Option kann Visual Studio Projektdaten zwischenspeichern, damit es, wenn Sie die Projekte das nächste Mal öffnen, die zwischengespeicherten Daten abrufen kann, statt sie erneut aus den Projektdateien berechnen zu müssen. Durch zwischengespeicherte Daten kann die Projektladezeit deutlich verringert werden.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Zusätzliche Features im Visual Studio Marketplace

Weitere Text-Editor-Features finden Sie in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Ein Beispiel ist [C++ Quick Fixes](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), das Folgendes unterstützt:

- **Add missing #include** - Schlägt zutreffende #include-Anweisungen für unbekannte Symbole in Ihrem Code vor.

- **Add using namespace/Fully qualify symbol** - Wie die vorherige Option, aber für Namespaces.

- **Add missing semicolon**

- **Onlinehilfe**: Durchsuchen Sie die Onlinehilfe nach Ihren Fehlermeldungen.

- Und mehr...

## <a name="see-also"></a>Siehe auch

- [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)
- [Umgestaltung in C++ (VC-Blog)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
