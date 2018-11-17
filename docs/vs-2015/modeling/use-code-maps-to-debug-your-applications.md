---
title: Verwenden von Code Maps zum Debuggen von Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, visualizing code
- Visual Studio Ultimate, navigating code visually
- Visual Studio Ultimate, understanding code
- Visual Studio Ultimate, mapping code relationships
- Visual Studio Ultimate, code maps
- mapping code relationships
- code maps
- mapping relationships in code
ms.assetid: 9fd0c9a2-d351-40c8-be88-0749788264bf
caps.latest.revision: 51
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: af5f34b307f94f1bae4c913421acbe0a934ed113
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743833"
---
# <a name="use-code-maps-to-debug-your-applications"></a>Verwenden von Code Maps zum Debuggen von Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Code Maps helfen Ihnen, die Übersicht in umfangreichen Codebasen, nicht vertrautem Code oder Legacycode zu behalten. Wenn Sie beispielsweise debuggen, müssen Sie sich möglicherweise Code in vielen Dateien und Projekten ansehen. Mithilfe von Code Maps können Sie in Codeabschnitten navigieren und Beziehungen zwischen ihnen verstehen. Auf diese Weise müssen Sie die den Code nicht gedanklich nachvollziehen oder ein separates Diagramm zeichnen. Wenn Sie die Arbeit unterbrechen müssen, können Code Maps Ihnen helfen, sich den Code wieder ins Gedächtnis zu rufen, an dem Sie arbeiten.  
  
 ![Code Map &#45; Zuordnen von Beziehungen im Code](../modeling/media/codemapstoryboardpaint.png "CodeMapStoryboardPaint")  
  
 **Ein grüner Pfeils zeigt, wo der Cursor im Editor angezeigt wird**  
  
 Details zu den Befehlen und Aktionen, die Sie bei der Arbeit mit Code Maps können, finden Sie unter [durchsuchen und Neuanordnen code Maps](../modeling/browse-and-rearrange-code-maps.md).  
  
## <a name="understand-the-problem"></a>Das Problem verstehen  
 Nehmen Sie an, in einem Zeichenprogramm, an dem Sie arbeiten, liegt ein Fehler vor. Um den Fehler zu reproduzieren, öffnen Sie die Projektmappe in Visual Studio, und drücken Sie **F5** mit dem Debuggen beginnen.  
  
 Wenn Sie eine Linie zeichnen, und wählen Sie **letzten Strich rückgängig machen**, geschieht nichts, bis Sie die nächste Zeile zeichnen.  
  
 ![Code Map &#45; Fehler reproduzieren](../modeling/media/codemapstoryboardpaint0.png "CodeMapStoryboardPaint0")  
  
 Daher beginnen Sie mit der Untersuchung, indem Sie nach der `Undo`-Methode suchen. Sie finden diese in der `PaintCanvas`-Klasse.  
  
 ![Code Map &#45; Suchen von Code](../modeling/media/codemapstoryboardpaint1.png "CodeMapStoryboardPaint1")  
  
## <a name="start-mapping-the-code"></a>Die Codezuordnung starten  
 Nun beginnen Sie mit dem Mapping der `undo`-Methode und ihrer Beziehungen. Fügen Sie im Code-Editor die `undo`-Methode und die Felder, auf die sie verweist, zu einer neuen Codezuordnung hinzu. Wenn Sie eine neue Zuordnung erstellen, kann es einige Zeit dauern, den Code zu indizieren. Aufgrund der Indizierung können spätere Vorgänge schneller ausgeführt werden.  
  
 ![Code Map &#45; -Methode und verwandte Felder anzeigen](../modeling/media/codemapstoryboardpaint3.png "CodeMapStoryboardPaint3")  
  
> [!TIP]
>  Die letzten zur Zuordnung hinzugefügten Elemente werden grün hervorgehoben. Anhand eines grünen Pfeils wird die Position des Cursors im Code angezeigt. Pfeile zwischen Elementen stellen verschiedene Beziehungen dar. Weitere Informationen zu Elementen in der Map enthalten die entsprechenden QuickInfos. Fahren Sie zur Anzeige einfach mit dem Mauszeiger über das Element.  
  
 ![Code Map &#45; Anzeigen von QuickInfos](../modeling/media/codemapstoryboardpaint4.png "CodeMapStoryboardPaint4")  
  
## <a name="navigate-and-examine-code-from-the-map"></a>Code aus der Zuordnung navigieren und untersuchen  
 Um die Codedefinition für jedes Feld anzuzeigen, doppelklicken Sie auf das Feld auf der Karte aus, oder wählen Sie das Feld, und drücken Sie **F12**. Der grüne Pfeil wird zwischen den Elementen in der Zuordnung verschoben. Der Cursor im Code-Editor wird automatisch ebenfalls bewegt.  
  
 ![Code Map &#45; Felddefinition untersuchen](../modeling/media/codemapstoryboardpaint5.png "CodeMapStoryboardPaint5")  
  
 ![Code Map &#45; Felddefinition untersuchen](../modeling/media/codemapstoryboardpaint5a.png "CodeMapStoryboardPaint5A")  
  
> [!TIP]
>  Sie können den grünen Pfeil in der Zuordnung auch verschieben, indem Sie den Cursor im Code-Editor bewegen.  
  
## <a name="understand-relationships-between-pieces-of-code"></a>Beziehungen zwischen Teilen des Codes verstehen  
 Nun möchten Sie wissen, in welchem anderen Code die Felder `history` und `paintObjects` verwendet werden. Sie können der Zuordnung alle Methoden hinzufügen, die auf diese Felder verweisen. Dies kann von der Map oder vom Code-Editor aus erfolgen.  
  
 ![Code Map &#45; "alle Verweise suchen"](../modeling/media/codemapstoryboardpaint6.png "CodeMapStoryboardPaint6")  
  
 ![Öffnen Sie eine codezuordnung im Code-Editor](../modeling/media/codemapstoryboardpaint6a.PNG "CodeMapStoryboardPaint6A")  
  
> [!NOTE]
>  Wenn Sie Elemente aus einem Projekt hinzufügen, das von mehreren Apps wie Windows Phone oder Windows Store gemeinsam genutzt wird, werden diese Elemente immer mit dem derzeit aktiven App-Projekt in der Map angezeigt. Wenn Sie also den Kontext auf ein anderes App-Projekt ändern, ändert sich auch der Kontext auf der Map für alle neu hinzugefügte Elemente aus dem freigegebenen Projekt. Vorgänge, die Sie mit einem Element in der Zuordnung ausführen, gelten nur für solche Elemente, die denselben Kontext gemeinsam verwenden.  
  
 Ändern Sie das Layout, um den Ablauf der Beziehungen neu anzuordnen und die Zuordnung besser lesbar zu machen. Sie können Elemente in der Zuordnung auch verschieben, indem Sie sie an andere Positionen ziehen.  
  
 ![Code Map &#45; Layout ändern](../modeling/media/codemapstoryboardpaint7a.png "CodeMapStoryboardPaint7A")  
  
> [!TIP]
>  In der Standardeinstellung **inkrementelles Layout** aktiviert ist. Dadurch wird die Zuordnung so wenig wie möglich neu angeordnet, wenn Sie neue Elemente hinzufügen. Um die gesamte Zuordnung jedes Mal, wenn Sie neue Elemente hinzufügen zu ändern, deaktivieren Sie **inkrementelles Layout**.  
  
 ![Code Map &#45; Layout ändern](../modeling/media/codemapstoryboardpaint7.png "CodeMapStoryboardPaint7")  
  
 Überprüfen Sie diese Methoden. Doppelklicken Sie auf der Karte, auf die **PaintCanvas** -Methode, oder wählen Sie diese Methode, und drücken Sie **F12**. Sie erfahren, dass `history` und `paintObjects` von dieser Methode als leere Listen erstellt werden.  
  
 ![Code Map &#45; Methodendefinition untersuchen](../modeling/media/codemapstoryboardpaint8.png "CodeMapStoryboardPaint8")  
  
 Wiederholen Sie nun die gleichen Schritte, um die Definition der `clear`-Methode zu überprüfen. Sie erfahren, dass in `clear` einige Aufgaben mit `paintObjects` und `history` ausgeführt werden. Anschließend wird die `Repaint`-Methode aufgerufen.  
  
 ![Code Map &#45; Methodendefinition untersuchen](../modeling/media/codemapstoryboardpaint9.png "CodeMapStoryboardPaint9")  
  
 Überprüfen Sie nun die Definition der `addPaintObject`-Methode. Darin werden ebenfalls einige Aufgaben mit `history` und `paintObjects` ausgeführt. Auch darin wird `Repaint` aufgerufen.  
  
 ![Code Map &#45; Methodendefinition untersuchen](../modeling/media/codemapstoryboardpaint10.png "CodeMapStoryboardPaint10")  
  
## <a name="find-the-problem-by-examining-the-map"></a>Das Problem durch Prüfen der Zuordnung suchen  
 Anscheinend wird von allen Methoden, die `history` und `paintObjects` ändern, `Repaint` aufgerufen. Von der `undo`-Methode wird `Repaint` jedoch nicht aufgerufen, obwohl von `undo` die gleichen Felder geändert werden. Daher denken Sie, dass Sie dieses Problem beheben können, indem Sie `Repaint` von `undo` aus aufrufen.  
  
 ![Code Map &#45; fehlenden Methodenaufruf suchen](../modeling/media/codemapstoryboardpaint11.png "CodeMapStoryboardPaint11")  
  
 Wenn Sie keine Zuordnung zur Verfügung gehabt hätten, in der dieser fehlende Aufruf angezeigt wird, wäre es möglicherweise schwieriger gewesen, dieses Problem zu finden, insbesondere bei komplexerem Code.  
  
## <a name="share-your-discovery-and-next-steps"></a>Ergebnisse freigeben und nächste Schritte  
 Bevor Sie oder jemand anderes diesen Fehler behebt, können Sie in der Zuordnung Notizen zu dem Problem und dessen Behebung erstellen.  
  
 ![Code Map &#45; Kommentieren und Elemente für weitere](../modeling/media/codemapstoryboardpaint12.png "CodeMapStoryboardPaint12")  
  
 Sie können der Zuordnung beispielsweise Kommentare hinzufügen und Elemente mit Farben kennzeichnen.  
  
 ![Code Map &#45; kommentiert und gekennzeichnete Elemente](../modeling/media/codemapstoryboardpaint12a.png "CodeMapStoryboardPaint12A")  
  
 Wenn Microsoft Outlook installiert ist, können Sie die Zuordnung per E-Mail an andere senden. Sie können die Zuordnung auch als Bild oder in einem anderen Format exportieren.  
  
 ![Code Map &#45; Freigabe, Export, e-Mail](../modeling/media/codemapstoryboardpaint13.png "CodeMapStoryboardPaint13")  
  
## <a name="fix-the-problem-and-show-what-you-did"></a>Das Problem beheben und zeigen, was Sie getan haben  
 Fügen Sie den Aufruf von `Repaint` zu `undo` hinzu, um diesen Fehler zu beheben.  
  
 ![Code Map &#45; fehlenden Methodenaufruf hinzufügen](../modeling/media/codemapstoryboardpaint14.png "CodeMapStoryboardPaint14")  
  
 Starten Sie die Debugsitzung neu, und versuchen Sie, den Fehler zu reproduzieren, um sicherzustellen, dass der Fehler behoben ist. Wählen jetzt **letzten Strich rückgängig machen** wie erwartet funktioniert, und bestätigen Sie die richtige Korrektur vorgenommen.  
  
 ![Code Map &#45; Codekorrektur bestätigen](../modeling/media/codemapstoryboardpaint15.png "CodeMapStoryboardPaint15")  
  
 Sie können die Zuordnung aktualisieren, damit die Ihre Korrektur angezeigt wird.  
  
 ![Code Map &#45; Update-Zuordnung mit fehlendem Methodenaufruf](../modeling/media/codemapstoryboardpaint16.png "CodeMapStoryboardPaint16")  
  
 Die Zuordnung wird nun ein Link zwischen **Rückgängig** und **Repaint**.  
  
 ![Code Map &#45; aktualisierte Zuordnung durch Methodenaufruf](../modeling/media/codemapstoryboardpaint17.png "CodeMapStoryboardPaint17")  
  
> [!NOTE]
>  Wenn Sie die Zuordnung aktualisieren, wird möglicherweise eine Meldung angezeigt, die besagt, dass der zum Erstellen der Zuordnung verwendete Codeindex aktualisiert wurde. Dies bedeutet, dass jemand den Code geändert hat, was dazu führt, dass die Zuordnung nicht mit dem aktuellen Code übereinstimmt. Das hindert Sie nicht daran, die Zuordnung zu aktualisieren. Sie müssen jedoch möglicherweise die Zuordnung neu erstellen, um sicherzustellen, dass sie dem Code entspricht.  
  
 Die Überprüfung ist nun abgeschlossen. Sie haben das Problem gefunden und erfolgreich korrigiert, indem Sie den Code zugeordnet haben. Außerdem verfügen Sie über eine Zuordnung, anhand der Sie im Code navigieren, sich an das Gelernte erinnern und die Schritte zur Behebung des Problems anzeigen können.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)   
 [Visualisieren von Code](../modeling/visualize-code.md)



