---
title: "Use code maps to debug your applications | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "Visual Studio Ultimate, visualizing code"
  - "Visual Studio Ultimate, navigating code visually"
  - "Visual Studio Ultimate, understanding code"
  - "Visual Studio Ultimate, mapping code relationships"
  - "Visual Studio Ultimate, code maps"
  - "mapping code relationships"
  - "code maps"
  - "mapping relationships in code"
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 49
author: "alexhomer1"
ms.author: "ahomer"
manager: "douge"
caps.handback.revision: 49
---
# Use code maps to debug your applications
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Code Maps helfen Ihnen, die Übersicht in umfangreichen Codebasen, nicht vertrautem Code oder Legacycode zu behalten.  Wenn Sie beispielsweise debuggen, müssen Sie sich möglicherweise Code in vielen Dateien und Projekten ansehen.  Mithilfe von Code Maps können Sie in Codeabschnitten navigieren und Beziehungen zwischen ihnen verstehen.  Auf diese Weise müssen Sie die den Code nicht gedanklich nachvollziehen oder ein separates Diagramm zeichnen.  Wenn Sie die Arbeit unterbrechen müssen, können Code Maps Ihnen helfen, sich den Code wieder ins Gedächtnis zu rufen, an dem Sie arbeiten.  
  
 ![Codezuordnung &#45; Beziehungen im Code zuordnen](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **Ein grüner Pfeils zeigt die Position des Cursors im Editor an.**  
  
 Weitere Informationen zu Befehlen und Aktionen für die Arbeit mit Code Maps finden Sie unter [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md).  
  
## Das Problem verstehen  
 Nehmen Sie an, in einem Zeichenprogramm, an dem Sie arbeiten, liegt ein Fehler vor.  Öffnen Sie die Projektmappe in Visual Studio, und drücken Sie **F5**, um das Debuggen zu starten und den Fehler zu reproduzieren.  
  
 Wenn Sie eine Linie zeichnen und **Letzten Strich rückgängig machen** auswählen, geschieht nichts, bis Sie die nächste Linie zeichnen.  
  
 ![Codezuordnung &#45; Fehler reproduzieren](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 Daher beginnen Sie mit der Untersuchung, indem Sie nach der `Undo`\-Methode suchen.  Sie finden diese in der `PaintCanvas`\-Klasse.  
  
 ![Codezuordnung &#45; Code suchen](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## Die Codezuordnung starten  
 Nun beginnen Sie mit dem Mapping der `undo`\-Methode und ihrer Beziehungen.  Fügen Sie im Code\-Editor die `undo`\-Methode und die Felder, auf die sie verweist, zu einer neuen Codezuordnung hinzu.  Wenn Sie eine neue Zuordnung erstellen, kann es einige Zeit dauern, den Code zu indizieren.  Aufgrund der Indizierung können spätere Vorgänge schneller ausgeführt werden.  
  
 ![Codezuordnung &#45; Methode und verwandte Felder anzeigen](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  Die letzten zur Zuordnung hinzugefügten Elemente werden grün hervorgehoben.  Anhand eines grünen Pfeils wird die Position des Cursors im Code angezeigt.  Pfeile zwischen Elementen stellen verschiedene Beziehungen dar.  Weitere Informationen zu Elementen in der Map enthalten die entsprechenden QuickInfos. Fahren Sie zur Anzeige einfach mit dem Mauszeiger über das Element.  
  
 ![Codezuordnung &#45; QuickInfo anzeigen](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## Code aus der Zuordnung navigieren und untersuchen  
 Doppelklicken Sie auf ein Feld in der Map, oder wählen Sie ein Feld aus, und drücken Sie **F12**, um die Codedefinition für einzelne Felder anzuzeigen.  Der grüne Pfeil wird zwischen den Elementen in der Zuordnung verschoben.  Der Cursor im Code\-Editor wird automatisch ebenfalls bewegt.  
  
 ![Codezuordnung &#45; Felddefinition untersuchen](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![Codezuordnung &#45; Felddefinition untersuchen](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  Sie können den grünen Pfeil in der Zuordnung auch verschieben, indem Sie den Cursor im Code\-Editor bewegen.  
  
## Beziehungen zwischen Teilen des Codes verstehen  
 Nun möchten Sie wissen, in welchem anderen Code die Felder `history` und `paintObjects` verwendet werden.  Sie können der Zuordnung alle Methoden hinzufügen, die auf diese Felder verweisen.  Dies kann von der Map oder vom Code\-Editor aus erfolgen.  
  
 ![Codezuordnung &#45; Alle Verweise suchen](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![Öffnen einer Codezuordnung aus dem Code&#45;Editor](../modeling/media/codemapstoryboardpaint6a.png "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  Wenn Sie Elemente aus einem Projekt hinzufügen, das von mehreren Apps wie Windows Phone oder Windows Store gemeinsam genutzt wird, werden diese Elemente immer mit dem derzeit aktiven App\-Projekt in der Map angezeigt.  Wenn Sie also den Kontext auf ein anderes App\-Projekt ändern, ändert sich auch der Kontext auf der Map für alle neu hinzugefügte Elemente aus dem freigegebenen Projekt.  Vorgänge, die Sie mit einem Element in der Zuordnung ausführen, gelten nur für solche Elemente, die denselben Kontext gemeinsam verwenden.  
  
 Ändern Sie das Layout, um den Ablauf der Beziehungen neu anzuordnen und die Zuordnung besser lesbar zu machen.  Sie können Elemente in der Zuordnung auch verschieben, indem Sie sie an andere Positionen ziehen.  
  
 ![Codezuordnung &#45; Layout ändern](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  Standardmäßig ist die Einstellung **Inkrementelles Layout** aktiviert.  Dadurch wird die Zuordnung so wenig wie möglich neu angeordnet, wenn Sie neue Elemente hinzufügen.  Deaktivieren Sie die Einstellung **Inkrementelles Layout**, um die gesamte Zuordnung jedes Mal neu anzuordnen, wenn Sie neue Elemente hinzufügen.  
  
 ![Codezuordnung &#45; Layout ändern](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 Überprüfen Sie diese Methoden.  Doppelklicken Sie in der Map auf die **PaintCanvas**\-Methode, oder wählen Sie diese Methode aus, und drücken Sie **F12**.  Sie erfahren, dass `history` und `paintObjects` von dieser Methode als leere Listen erstellt werden.  
  
 ![Codezuordnung &#45; Methodendefinition untersuchen](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 Wiederholen Sie nun die gleichen Schritte, um die Definition der `clear`\-Methode zu überprüfen.  Sie erfahren, dass in `clear` einige Aufgaben mit `paintObjects` und `history` ausgeführt werden.  Anschließend wird die `Repaint`\-Methode aufgerufen.  
  
 ![Codezuordnung &#45; Methodendefinition untersuchen](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 Überprüfen Sie nun die Definition der `addPaintObject`\-Methode.  Darin werden ebenfalls einige Aufgaben mit `history` und `paintObjects` ausgeführt.  Auch darin wird `Repaint` aufgerufen.  
  
 ![Codezuordnung &#45; Methodendefinition untersuchen](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## Das Problem durch Prüfen der Zuordnung suchen  
 Anscheinend wird von allen Methoden, die `history` und `paintObjects` ändern, `Repaint` aufgerufen.  Von der `undo`\-Methode wird `Repaint` jedoch nicht aufgerufen, obwohl von `undo` die gleichen Felder geändert werden.  Daher denken Sie, dass Sie dieses Problem beheben können, indem Sie `Repaint` von `undo` aus aufrufen.  
  
 ![Codezuordnung &#45; Fehlenden Methodenaufruf suchen](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 Wenn Sie keine Zuordnung zur Verfügung gehabt hätten, in der dieser fehlende Aufruf angezeigt wird, wäre es möglicherweise schwieriger gewesen, dieses Problem zu finden, insbesondere bei komplexerem Code.  
  
## Ergebnisse freigeben und nächste Schritte  
 Bevor Sie oder jemand anderes diesen Fehler behebt, können Sie in der Zuordnung Notizen zu dem Problem und dessen Behebung erstellen.  
  
 ![Codezuordnung &#45; Elemente zur Nachverfolgung kommentieren und kennzeichnen](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 Sie können der Zuordnung beispielsweise Kommentare hinzufügen und Elemente mit Farben kennzeichnen.  
  
 ![Codezuordnung &#45; Kommentierte und gekennzeichnete Elemente](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Wenn Microsoft Outlook installiert ist, können Sie die Zuordnung per E\-Mail an andere senden.  Sie können die Zuordnung auch als Bild oder in einem anderen Format exportieren.  
  
 ![Codezuordnung &#45; Freigabe, Export, E&#45;Mail&#45;Sendung](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## Das Problem beheben und zeigen, was Sie getan haben  
 Fügen Sie den Aufruf von `Repaint` zu `undo` hinzu, um diesen Fehler zu beheben.  
  
 ![Codezuordnung &#45; Fehlenden Methodenaufruf hinzufügen](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 Starten Sie die Debugsitzung neu, und versuchen Sie, den Fehler zu reproduzieren, um sicherzustellen, dass der Fehler behoben ist.  Wenn Sie nun **Letzten Strich rückgängig machen** auswählen, wird diese Funktion wie erwartet ausgeführt und damit bestätigt, dass Sie die richtige Korrektur vorgenommen haben.  
  
 ![Codezuordnung &#45; Codekorrektur bestätigen](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 Sie können die Zuordnung aktualisieren, damit die Ihre Korrektur angezeigt wird.  
  
 ![Codezuordnung &#45; Zuordnung mit fehlendem Methodenaufruf aktualisieren](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 In der Zuordnung wird nun ein Link zwischen **undo** und **Repaint** angezeigt.  
  
 ![Codezuordnung &#45; Durch Methodenaufruf aktualisierte Zuordnung](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  Wenn Sie die Zuordnung aktualisieren, wird möglicherweise eine Meldung angezeigt, die besagt, dass der zum Erstellen der Zuordnung verwendete Codeindex aktualisiert wurde.  Dies bedeutet, dass jemand den Code geändert hat, was dazu führt, dass die Zuordnung nicht mit dem aktuellen Code übereinstimmt.  Das hindert Sie nicht daran, die Zuordnung zu aktualisieren. Sie müssen jedoch möglicherweise die Zuordnung neu erstellen, um sicherzustellen, dass sie dem Code entspricht.  
  
 Die Überprüfung ist nun abgeschlossen.  Sie haben das Problem gefunden und erfolgreich korrigiert, indem Sie den Code zugeordnet haben.  Außerdem verfügen Sie über eine Zuordnung, anhand der Sie im Code navigieren, sich an das Gelernte erinnern und die Schritte zur Behebung des Problems anzeigen können.  
  
## Siehe auch  
 [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Visualize code](../modeling/visualize-code.md)