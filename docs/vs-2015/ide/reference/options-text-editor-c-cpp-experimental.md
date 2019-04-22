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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0e0fdfc710abfc40005f3480e66b4411e93d0623
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654723"
---
# <a name="options-text-editor-cc-experimental"></a>Optionen, Text-Editor, C/C++, Experimentell
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie diese Optionen ändern, können Sie beim Programmieren in C oder C++ das Verhalten ändern, das mit IntelliSense und der Suchdatenbank zusammenhängt.  
  
 Um auf diese Seite zuzugreifen, erweitern Sie im Dialogfeld **Optionen** im linken Bereich den Eintrag **Text-Editor**, erweitern Sie **C/C++**, und wählen Sie dann **Experimental**aus.  
  
 Diese Features sind in einer Visual Studio 2015 Update 1 RC-Installation verfügbar.  
  
> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Informationen hierzu finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio)](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Durchsuchen/Navigation  
 **Neue Datenbank-Engine aktivieren**  
 Dadurch sollten automatisch das Auffüllen einer Datenbank sowie alle Datenbankvorgänge für Vorgänge wie etwa **Gehe zu Definition** und **Alle Verweise suchen**(ohne Genauigkeitsverlust) beschleunigt werden. (Sie müssen Ihre Projektmappe nur schließen und erneut öffnen , um die Änderungen anzuwenden. Es ist nicht erforderlich, Visual Studio neu zu starten.)  
  
## <a name="intellisense"></a>IntelliSense  
 **Punkt in Pfeil in der Memberliste aktivieren**  
 Ersetzt „.“ durch „->“, sofern dies für die Memberliste anwendbar ist.  
  
## <a name="refactoring"></a>Umgestaltung  
 **Extraktionsfunktion aktivieren**  
 Ausgewählter Code wird in seine eigene Funktion extrahiert, und der Code wird durch einen Aufruf der neuen Funktion ersetzt. Um auf dieses Feature zuzugreifen, klicken Sie mit der rechten Maustaste auf den ausgewählten Code, und wählen Sie **Schnelle Aktionen**aus, oder drücken Sie einfach die Standardtastenkombination STRG + Punkt [STRG + .].  
  
 **Ändern der Signatur aktivieren**  
 Parameter einer Funktion können hinzugefügt, neu angeordnet und gelöscht werden, und die Änderungen werden an alle Aufrufsites weitergegeben. Um auf dieses Feature zuzugreifen, klicken Sie mit der rechten Maustaste auf irgendeinen Aufruf der Funktion, und wählen Sie **Schnelle Aktionen**aus, oder drücken Sie einfach die Standardtastenkombination STRG + Punkt [STRG + .].  
  
## <a name="text-editor"></a>Text-Editor  
 **Erweiterungsbereiche aktivieren**  
 Ist diese Option aktiviert, können Sie markierten Text in geschweifte Klammern setzen, indem Sie '{' im Text-Editor eingeben.  
  
 **Erweiterungsrangfolge aktivieren**  
 Ist diese Option aktiviert, können Sie markierten Text in runde Klammern setzen, indem Sie '(' im Text-Editor eingeben.  
  
 Weitere Text-Editor-Features für die Visual Studio Gallery finden Sie in der Liste [hier](http://go.microsoft.com/fwlink/?LinkId=692016). Ein Beispiel ist [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), das Folgendes unterstützt:  
  
- **Add missing #include** - Schlägt zutreffende #include-Anweisungen für unbekannte Symbole in Ihrem Code vor.  
  
- **Add using namespace/Fully qualify symbol** - Wie die vorherige Option, aber für Namespaces.  
  
- **Add missing semicolon**  
  
- **MSDN Help** - In MSDN nach Fehlermeldungen suchen.  
  
  Sie können entweder mit dem Mauszeiger auf eine Wellenlinie zeigen, um eine Glühbirne anzuzeigen, oder die Standardtastenkombination Strg + Punkt (STRG + .) verwenden. Für die Tastenkombination muss die Einfügemarke nicht auf dem speziellen Fehler oder Token positioniert werden. Es genügt, wenn Sie sich in der Zeile befinden, in der der Fehler auftritt, um Vorschläge für alle Elemente in dieser Zeile aufzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)   
 [Umgestaltung in C++ (VC-Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
