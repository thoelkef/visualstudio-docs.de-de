---
title: Erstellen einer visuellen Zuordnung der Aufrufliste | Microsoft-Dokumentation
ms.date: 11/26/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5285149bbefa8230940cfad19b5e0391a1e99bd
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690501"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Erstellen von einer visuellen Zuordnung der Aufrufliste beim Debuggen (C#, Visual Basic, C++, JavaScript)

Erstellen Sie eine Code Map, um die Aufrufliste während des Debuggens visuell zu verfolgen. Sie können Notizen auf der Code Map vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.

Eine exemplarische Vorgehensweise die diesem Video aus: [Video: Debuggen Sie visuelles mit Code Map-debuggerintegration (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

Details zu Befehlen und Aktionen, die Sie mit Code Maps verwenden können, finden Sie unter [durchsuchen und Neuanordnen code Maps](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Sie können Erstellen von Code maps nur in [Visual Studio Enterprise-Edition](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017).

So sieht ein kurzen Blick auf eine Code Map aus:

 ![Debuggen mit Aufruflisten in Code Maps](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

##  <a name="MapStack"></a> Abbilden der Aufrufliste

1. In einem Visual Studio Enterprise C#, Visual Basic, C++ oder JavaScript-Projekt, das Debuggen starten, indem Sie die Auswahl **Debuggen** > **Debuggen starten** oder durch Drücken **F5**.
   
1. Wählen Sie nach Ihrer app in den Unterbrechungsmodus wechselt oder Sie eine Funktion schrittweise, **Debuggen** > **Code Map**, oder drücken Sie **STRG**+**UMSCHALT** +**`**.

   Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:

   ![Finden Sie in der Aufrufliste auf Code Map](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Der Code zuordnen Updates automatisch, wenn Sie mit dem Debuggen fortfahren. Ändern kartenelemente oder Layout wirkt sich nicht auf den Code in keiner Weise aus. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.

Zeigen Sie darauf, und sehen Sie sich die QuickInfo des jeweiligen Elements, um weitere Informationen zu einem Element zu erhalten. Sie können auch auswählen, **Legende** auf der Symbolleiste, um zu erfahren, was bedeutet, dass jedes Symbol.

![Kartenlegende Code](../debugger/media/debuggermap_showlegend.png "Code Kartenlegende")

>[!NOTE]
>Die Nachricht **kann das Diagramm basiert auf einer älteren Version des Codes** am oberen Rand der Code Map also der Code möglicherweise geändert wurden, nachdem Sie die Zuordnung zuletzt aktualisiert. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.

## <a name="map-external-code"></a>Externer Code Map

Standardmäßig wird nur Ihr eigener Code in der Zuordnung angezeigt. Um externen Code auf der Karte anzuzeigen:
  
- Mit der rechten Maustaste den **Aufrufliste** Fenster, und wählen **externen Code anzeigen**:
  
  ![Anzeige von externem Code über das Fenster "Aufrufliste"](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- Oder, deaktivieren Sie **nur meinen Code aktivieren** in Visual Studio **Tools** (oder **Debuggen**) > **Optionen**  >   **Debuggen von**:
  
  ![Anzeigen von externem Code über Dialogfeld "Optionen"](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Steuern Sie das Layout der Zuordnung

Ändern das Layout der Zuordnung wirkt sich nicht auf den Code in keiner Weise aus. 

Um das Layout der Zuordnung steuern möchten, wählen Sie die **Layout** Menü auf der Symbolleiste der Map. 

In der **Layout** Menü können Sie:

-   Ändern Sie das Standardlayout.
-   Beenden Sie die Zuordnung durch Aufheben der Auswahl automatisch neu anordnen **Automatisches Layout beim Debugging**.
-   Die Zuordnung so wenig wie möglich neu anzuordnen, wenn Sie Elemente, wählen Sie hierzu von hinzufügen **inkrementelles Layout**.

##  <a name="MakeNotes"></a> Erstellen von Notizen zum Code

Sie können Kommentare, um nachzuverfolgen, was geschieht im Code hinzufügen. 

Um einen Kommentar hinzuzufügen, mit der rechten Maustaste in die Code Map, und wählen Sie **bearbeiten** > **neuer Kommentar**, geben Sie dann den Kommentar. 

Um eine neue Zeile in einem Kommentar hinzuzufügen, drücken Sie die **UMSCHALT**+**EINGABETASTE**.

 ![Kommentar zu Aufrufliste in Code Map hinzufügen](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> Aktualisieren der Code Map mit der nächsten Aufrufliste

Wie Sie Ihre app in eine Funktion zum nächsten Haltepunkt oder Schritt ausführen, wird die Zuordnung neue Aufruflisten automatisch hinzugefügt.

![Update Code Map mit nächster Aufrufliste](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Wählen Sie zum Beenden der Zuordnung neue Aufruflisten automatisch hinzufügt ![anzeigen Aufrufliste auf Code Map automatisch](../debugger/media/debuggermap_automaticupdateicon.gif "anzeigen Aufrufliste auf Code Map automatisch") auf der Symbolleiste der Codeübersicht. Die Zuordnung weiterhin vorhandene Aufruflisten zu markieren. Um die aktuelle Aufrufliste manuell zur Karte hinzufügen möchten, drücken Sie die **STRG**+**UMSCHALT**+**`**. 

##  <a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Code Map

Nun, da Sie in einer Karte haben C# oder Visual Basic können Sie Elemente wie Felder, Eigenschaften und andere Methoden, um nachzuverfolgen, was geschieht im Code hinzufügen. 

Um die Definition einer Methode im Code aufzurufen, doppelklicken Sie auf die Methode in der Zuordnung, oder wählen Sie ihn, und drücken Sie **F12**, oder der rechten Maustaste darauf und wählen Sie **Gehe zu Definition**.

![Wechseln Sie zu der Codedefinition für eine Methode auf Code Map](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Klicken Sie zum Hinzufügen von Elementen, die Sie auf der Karte nachverfolgen möchten, mit der rechten Maustaste einer Methode, und wählen Sie die Elemente, die Sie nachverfolgen möchten. Die zuletzt hinzugefügten Elemente werden grün dargestellt.

![Felder im Zusammenhang mit einer Methode auf Aufruflisten-Code Map](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. Sie können diese Funktion deaktivieren und aktivieren durch Auswählen der **übergeordnete Elemente einschließen** Schaltfläche auf der Symbolleiste der Codeübersicht oder durch Drücken von **STRG** während Sie Elemente hinzufügen.

![Anzeigen von Feldern in einer Methode für die Aufruflisten-Code Map](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.

 ![Methoden, die ein Feld verwenden: Aufruflisten-Code Map](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Methoden, mit denen ein Feld in der Aufruflisten-Code Map](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> Suchen von Fehlern mithilfe der Code Map
 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Nehmen wir beispielsweise an, dass Sie einen Fehler in einer Zeichnung app untersuchen. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.

 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:

 ![Fügen Sie weitere Aufrufliste zu Code Map](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.

 Nachdem Sie den Fehler beheben und die app weiter auszuführen, wird die Zuordnung fügt den neuen Aufruf von `undo` zu `Repaint`:

 ![Hinzufügen der neuen Methode Methodenaufruf zu Aufrufliste in Code Map](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Freigeben Sie die Zuordnung für andere Benutzer.

Sie können eine Zuordnung zu exportieren, an andere Benutzer mit Microsoft Outlook senden, speichern Sie sie in der Projektmappe und checken Sie es in der Versionskontrolle.

Verwenden Sie zum Freigeben oder speichern Sie die Zuordnung, **freigeben** in der Symbolleiste der Codeübersicht. 

![Freigabe Aufruflisten-Code Map für andere Benutzer](../debugger/media/debuggermap_sharewithothers.png "Freigabe Aufruflisten-Code Map für andere Benutzer")

## <a name="see-also"></a>Siehe auch
[Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

[Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)

[Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
