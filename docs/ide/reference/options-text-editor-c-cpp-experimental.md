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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 3f5ddf5a42199c8097e982c6ddd8e559185787fb
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672339"
---
# <a name="options-text-editor-cc-experimental"></a>Optionen, Text-Editor, C/C++, Experimentell

Wenn Sie diese Optionen ändern, können Sie beim Programmieren in C oder C++ das Verhalten ändern, das mit IntelliSense und der Suchdatenbank zusammenhängt. Diese Features sind rein experimentell und werden möglicherweise in einer zukünftigen Version geändert oder komplett aus Visual Studio entfernt. In diesem Thema werden die Optionen in Visual Studio 2017 beschrieben. Wenn Sie Visual Studio 2015 verwenden, wählen Sie in der Auswahl oberhalb des Inhaltsverzeichnisses **2015** aus.

Drücken Sie **STRG + Q**, um `Quick Launch` zu aktivieren, und geben Sie anschließend „experimentell“ ein, um auf diese Eigenschaftenseite zuzugreifen. Der Schnellstart findet die Seite nach den ersten Buchstaben. Sie können auch darauf zugreifen, indem Sie **Tool | Optionen** auswählen, den **Text-Editor** und **C/C++** erweitern und anschließend **Experimentell** auswählen.

Diese Features sind mit einer Visual Studio 2017-Installation verfügbar.

> [!NOTE]
> Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Aktivieren von Predictive IntelliSense

Predictive IntelliSense beschränkt die Anzahl von angezeigten Ergebnissen in der Dropdownliste in IntelliSense, sodass nur für Ihren Kontext relevante Ergebnisse angezeigt werden. Wenn Sie z.B. <code>int x =</code> eingeben und das Dropdownmenü in IntelliSense aufrufen, werden Ihnen nur Integer oder Funktionen angezeigt, die Integer zurückgeben. Standardmäßig ist Predictive IntelliSense deaktiviert.

## <a name="enable-faster-project-load"></a>Aktivieren von „Schnelleres Laden von Projekten“

**Visual Studio 2017 15,3 und höher**: Diese Funktion heißt jetzt **Zwischenspeichern des Projekts aktivieren** und wurde auf die Eigenschaftenseite [VC++-Projekteinstellungen](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) verschoben.
Durch diese Option kann Visual Studio Projektdaten zwischenspeichern, damit es, wenn Sie die Projekte das nächste Mal öffnen, die zwischengespeicherten Daten abrufen kann, statt sie erneut aus den Projektdateien berechnen zu müssen. Durch zwischengespeicherte Daten kann die Projektladezeit deutlich verringert werden.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Zusätzliche Features im Visual Studio Marketplace

Weitere Text-Editor-Features finden Sie in [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Ein Beispiel ist [C++ Quick Fixes](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), das Folgendes unterstützt:

- **Add missing #include** - Schlägt zutreffende #include-Anweisungen für unbekannte Symbole in Ihrem Code vor.

- **Add using namespace/Fully qualify symbol** - Wie die vorherige Option, aber für Namespaces.

- **Add missing semicolon**

- **Onlinehilfe**: Durchsuchen Sie die Onlinehilfe nach Ihren Fehlermeldungen.

- Und mehr...

## <a name="see-also"></a>Siehe auch

- [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)
- [Umgestaltung in C++ (VC-Blog)](https://blogs.msdn.microsoft.com/vcblog/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview/)
