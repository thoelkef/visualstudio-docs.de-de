---
title: Erstellen einer visuellen Karte der aufrufsstapel | Microsoft-Dokumentation
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
ms.openlocfilehash: 135c7c66c9c6602f8c2e32bbdc1ba6e2fd28f548
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911517"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Erstellen einer visuellen Karte der aufrufsstapel während desC#Debuggens C++(, Visual Basic,, JavaScript)

Erstellen Sie eine Code Map, um die Aufrufliste während des Debuggens visuell zu verfolgen. Sie können Notizen auf der Code Map vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.

Eine exemplarische Vorgehensweise die diesem Video aus: [Video. Debuggen Sie visuelles mit Code Map-debuggerintegration (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

Ausführliche Informationen zu Befehlen und Aktionen, die Sie mit Code Maps verwenden können, finden Sie unter [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Code Maps können nur in [Visual Studio Enterprise Edition](https://visualstudio.microsoft.com/downloads)erstellt werden.

Es folgt ein kurzer Blick auf eine Code Map:

 ![Debuggen mit Aufruf Listen in Code Maps](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="MapStack"></a> Abbilden der Aufrufliste

1. Starten Sie in C#einem Visual Studio Enterprise- C++, Visual Basic-,-oder JavaScript-Projekt das Debuggen, indem **Sie Debuggen > ** **Debugging starten** oder **F5**drücken.

1. Wenn die app in den Unterbrechungs Modus wechselt oder Sie eine Funktion schrittweise ausführen, wählen Sie > **Code Map** **Debuggen** , oder drücken Sie **STRG**+**UMSCHALT**+ **`** .

   Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:

   ![Weitere Informationen finden Sie unter Code Map](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Der Code Map wird automatisch aktualisiert, wenn Sie das Debugging fortsetzen. Das Ändern von Karten Elementen oder des Layouts wirkt sich nicht auf den Code aus. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.

Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo des Elements an. Sie können auch **Legende** in der Symbolleiste auswählen, um zu erfahren, was die einzelnen Symbole bedeuten.

![Code Map-Legende](../debugger/media/debuggermap_showlegend.png "Code Map-Legende")

>[!NOTE]
>Die Meldung **das Diagramm basiert möglicherweise auf einer älteren Version des Codes** am Anfang der Code Map bedeutet, dass der Code nach der letzten Aktualisierung der Zuordnung geändert werden kann. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.

## <a name="map-external-code"></a>Externen Code zuordnen

Standardmäßig wird nur Ihr eigener Code in der Zuordnung angezeigt. So zeigen Sie externen Code auf der Karte an:

- Klicken Sie **mit der rechten** Maustaste in das Fenster "Fenster", und wählen Sie **externen Code anzeigen**:

  ![Anzeigen von externem Code mithilfe des Fensters "Fenster" aufrufen](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- Deaktivieren Sie alternativ **nur eigenen Code** in Visual Studio- **Tools** aktivieren (oder **Debuggen**) > **Optionen** > **Debuggen**:

  ![Externen Code mithilfe des Dialog Felds "Optionen" anzeigen](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Steuern des Kartenlayouts

Das Ändern des Kartenlayouts wirkt sich nicht auf den Code aus.

Um das Layout der Karte zu steuern, wählen Sie das **Layoutmenü** auf der Symbolleiste der Karte aus.

Im **Layoutmenü** können Sie folgende Aktionen ausführen:

- Ändern Sie das Standardlayout.
- Beenden Sie das erneute Anordnen der Zuordnung, indem Sie das **automatische Layout beim Debuggen**deaktivieren.
- Ordnen Sie die Zuordnung so wenig wie möglich neu an, wenn Sie Elemente hinzufügen, indem Sie das **inkrementelle Layout**deaktivieren.

## <a name="MakeNotes"></a> Erstellen von Notizen zum Code

Sie können Kommentare hinzufügen, um zu verfolgen, was im Code geschieht.

Um einen Kommentar hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Code Map, und wählen Sie > **neuen Kommentar** **Bearbeiten** aus, und geben Sie den Kommentar ein.

Um eine neue Zeile in einem Kommentar hinzuzufügen, drücken Sie **UMSCHALT**+**Eingabe**Taste.

 ![Kommentar zur aufrufsstapel auf Code Map hinzufügen](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Aktualisieren der Code Map mit der nächsten Aufrufliste

Wenn Sie die APP bis zum nächsten Breakpoint ausführen oder in eine Funktion springen, werden von der Zuordnung automatisch neue Aufruf Listen hinzugefügt.

![Code Map mit nächster aufrufsstapel aktualisieren](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Um zu verhindern, dass die Zuordnung automatisch neue Aufruf Listen hinzufügt, wählen Sie auf der Code Map Symbolleiste ![automatisch Aufruf Stapel auf Code Map anzeigen](../debugger/media/debuggermap_automaticupdateicon.gif "Aufrufsstapel auf Code Map automatisch anzeigen") aus. In der Karte werden auch weiterhin vorhandene Aufruf Listen hervorgehoben. Wenn Sie die aktuelle aufrufsstapel der Zuordnung manuell hinzufügen möchten, drücken Sie **STRG**+**UMSCHALT**+ **`** .

## <a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Code Map

Nachdem Sie nun über eine Karte verfügen, in C# oder Visual Basic, können Sie Elemente wie Felder, Eigenschaften und andere Methoden hinzufügen, um zu verfolgen, was im Code geschieht.

Um zur Definition einer Methode im Code zu wechseln, doppelklicken Sie auf die Methode in der Zuordnung, oder wählen Sie Sie aus, und drücken Sie **F12**, oder klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Gehe zu Definition**aus.

![Wechseln Sie zur Code Definition für eine Methode auf Code Map](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Klicken Sie mit der rechten Maustaste auf eine Methode, und wählen Sie die Elemente aus, die Sie nachverfolgen möchten, um der Zuordnung Elemente hinzuzufügen, die Sie verfolgen möchten. Die zuletzt hinzugefügten Elemente werden grün angezeigt.

![Felder, die mit einer Methode in der Code Map der](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. Sie können diese Funktion deaktivieren und aktivieren, indem Sie die Schaltfläche übergeordnete Elemente **einschließen** auf der Code Map Symbolleiste auswählen oder indem Sie **STRG** drücken, während Sie Elemente hinzufügen.

![Felder in einer Methode in der Code Map der anzeigen](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.

 ![Weitere Informationen finden Sie unter Methoden, die ein Feld verwenden: Code Map der](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Methoden, die ein Feld in der aufrufsstapel Code map verwenden](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Suchen von Fehlern mithilfe der Code Map
 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Angenommen, Sie untersuchen einen Fehler in einer Zeichnungs-app. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.

 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:

 ![Hinzufügen einer weiteren aufrufsstapel zu Code Map](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.

 Nachdem Sie den Fehler behoben und die Ausführung der APP fortgesetzt haben, fügt die Karte den neuen `undo` `Repaint`hinzu:

 ![Neuen Methodenaufrufe für die aufrufsstapel Code Map hinzufügen](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Freigeben der Zuordnung für andere Benutzer

Sie können eine Zuordnung exportieren, an andere Personen mit Microsoft Outlook senden, Sie in der Projekt Mappe speichern und Sie in die Versionskontrolle einchecken.

Wenn Sie die Zuordnung freigeben oder speichern möchten, verwenden Sie die **Freigabe** auf der Code Map Symbolleiste.

![Aufrufsstapel Code Map für andere freigeben](../debugger/media/debuggermap_sharewithothers.png "Aufruflisten-Code Map für andere Benutzer freigeben")

## <a name="see-also"></a>Siehe auch
[Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)

[Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)

[Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
