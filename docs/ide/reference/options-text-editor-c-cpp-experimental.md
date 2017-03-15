---
title: Optionen, Text-Editor, C/C++, Experimentell | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a1edc88394193474b273968d8435e8df06415044
ms.openlocfilehash: a3fcafe5c191987668dc6e0dce8835d748742ed7

---
# <a name="options-text-editor-cc-experimental"></a>Optionen, Text-Editor, C/C++, Experimentell
Wenn Sie diese Optionen ändern, können Sie beim Programmieren in C oder C++ das Verhalten ändern, das mit IntelliSense und der Suchdatenbank zusammenhängt.  
  
 Um auf diese Seite zuzugreifen, erweitern Sie im Dialogfeld **Optionen** im linken Bereich den Eintrag **Text-Editor**, erweitern Sie **C/C++**, und wählen Sie dann **Experimental**aus.  
  
 Diese Features sind in einer Visual Studio 2015 Update 1 RC-Installation verfügbar.  
  
> [!NOTE]
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Informationen hierzu finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio)](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Durchsuchen/Navigation  
 **Neues Datenbankmodul aktivieren**  
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
  
-   **Add missing #include** - Schlägt zutreffende #include-Anweisungen für unbekannte Symbole in Ihrem Code vor.  
  
-   **Add using namespace/Fully qualify symbol** - Wie die vorherige Option, aber für Namespaces.  
  
-   **Fehlendes Semikolon hinzufügen**  
  
-   **MSDN Help** - In MSDN nach Fehlermeldungen suchen.  
  
 Sie können entweder mit dem Mauszeiger auf eine Wellenlinie zeigen, um eine Glühbirne anzuzeigen, oder die Standardtastenkombination Strg + Punkt (STRG + .) verwenden. Für die Tastenkombination muss die Einfügemarke nicht auf dem speziellen Fehler oder Token positioniert werden. Es genügt, wenn Sie sich in der Zeile befinden, in der der Fehler auftritt, um Vorschläge für alle Elemente in dieser Zeile aufzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von sprachspezifischen Editor-Optionen](../../ide/reference/setting-language-specific-editor-options.md)   
 [Umgestaltung in C++ (VC-Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)



<!--HONumber=Feb17_HO4-->


