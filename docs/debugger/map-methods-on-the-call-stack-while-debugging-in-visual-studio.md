---
title: Erstellen einer visuellen Zuordnung der Aufrufliste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/18/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6156be294c9b64c26a7488aef3f0c92d1f4ccffd
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2018
ms.locfileid: "36296060"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-in-visual-studio-enterprise"></a>Erstellen von einer visuellen Zuordnung der Aufrufliste beim Debuggen in Visual Studio Enterprise
Erstellen Sie eine Code Map, um die Aufrufliste während des Debuggens visuell zu verfolgen. Sie können Notizen auf der Zuordnung vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.

 Sie benötigen Folgendes:

-   [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

-   Code, den Sie, z. B. Visual c#, Visual Basic, C++, JavaScript oder X++ Debuggen können

So sieht ein kurzen Blick auf eine Code Map aus:

 ![Debuggen mit Aufruflisten in Code Maps](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

 Thema

-   [Video: Debuggen Sie visuelles mit der Code Map-debuggerintegration (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

-   [Zuordnen der Aufrufliste](#MapStack)

-   [Aufzeichnen von Notizen zum code](#MakeNotes)

-   [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap)

-   [Hinzufügen von zugehörigem Code zur Zuordnung](#AddRelatedCode)

-   [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs)

-   [HÄUFIG GESTELLTE FRAGEN](#QA)

 Details zu den Befehlen und Aktionen, die Sie bei der Arbeit mit Code Maps können, finden Sie unter [durchsuchen und Neuanordnen code Maps](../modeling/browse-and-rearrange-code-maps.md).

##  <a name="MapStack"></a> Zuordnen der Aufrufliste

1.  Beginnen Sie mit dem Debuggen. (Tastatur: **F5**)

2.  Wählen Sie nach Ihrer app in den Unterbrechungsmodus wechselt oder Sie eine Funktion schrittweise, **Code Map**. (Tastatur: **STRG** + **UMSCHALT** + **`**)

     ![Wählen Sie die Code Map, um aufruflistenzuordnung zu starten](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:

     ![Finden Sie in der Aufrufliste auf Code Map](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Die Map wird beim Debuggen automatisch aktualisiert. Finden Sie unter [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap).

##  <a name="MakeNotes"></a> Aufzeichnen von Notizen zum code
 Fügen Sie Kommentare, um nachzuverfolgen, was im Code geschieht. Um eine neue Zeile in einem Kommentar hinzuzufügen, drücken Sie die **Umschalt + Eingabe**.

 ![Kommentar zu Aufrufliste in Code Map hinzufügen](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> Aktualisieren der Zuordnung mit der nächsten Aufrufliste
 Führen Sie die Anwendung bis zum nächsten Haltepunkt aus, oder führen Sie eine Funktion schrittweise aus. Die Zuordnung fügt eine neue Aufrufliste hinzu.

 ![Update Code Map mit nächster Aufrufliste](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

##  <a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Zuordnung
 Jetzt haben Sie einer Karte – was geschieht als Nächstes? Wenn Sie mit Visual c# oder Visual Basic arbeiten, fügen Sie Elemente wie Felder, Eigenschaften und andere Methoden, um nachzuverfolgen, was im Code geschieht.

 Doppelklicken Sie auf eine Methode, um ihre Codedefinition anzuzeigen, oder verwenden Sie das Kontextmenü für die Methode. (Tastatur: Wählen Sie die Methode auf der Karte, und drücken Sie **F12**)

 ![Wechseln Sie zu der Codedefinition für eine Methode auf Code Map](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Fügen Sie die Elemente hinzu, die Sie in der Zuordnung nachverfolgen möchten.

 ![Anzeigen von Feldern in einer Methode für die Aufruflisten-Code Map](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
>  Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. Dies ist, zwar hilfreich Sie können einfach halten, die Zuordnung durch Deaktivieren dieser Funktion mit dem **übergeordnete Elemente einschließen** Schaltfläche auf der Symbolleiste der Map oder durch Drücken von **STRG** beim Hinzufügen von Elementen.

 ![Felder im Zusammenhang mit einer Methode auf Aufruflisten-Code Map](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

 Hier können Sie leicht erkennen, welche Methoden die gleichen Felder verwenden. Die zuletzt hinzugefügten Elemente werden grün dargestellt.

 Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.

 ![Methoden, die ein Feld verwenden: Aufruflisten-Code Map](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Methoden, mit denen ein Feld in der Aufruflisten-Code Map](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> Suchen von Fehlern mithilfe der Zuordnung
 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Nehmen wir beispielsweise an, dass Sie einen Fehler in einem Zeichenprogramm untersuchen. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.

 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:

 ![Fügen Sie weitere Aufrufliste zu Code Map](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.

 Nachdem Sie den Fehler korrigiert haben und die Ausführung des Programms fortsetzen, fügt die Zuordnung den neuen Aufruf von `undo` zur `Repaint`-Funktion hinzu:

 ![Hinzufügen der neuen Methode Methodenaufruf zu Aufrufliste in Code Map](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

##  <a name="QA"></a> Fragen und Antworten

-   **Nicht alle Aufrufe, die auf der Karte angezeigt werden. Warum?**

     Standardmäßig wird nur Ihr eigener Code in der Zuordnung angezeigt. Um externen Code anzuzeigen, aktivieren Sie ihn im der **Aufrufliste** Fenster:

     ![Anzeige von externem Code über das Fenster "Aufrufliste"](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")

     oder deaktivieren Sie **nur meinen Code aktivieren** im Visual Studio-Debugoptionen:

     ![Anzeigen von externem Code über Dialogfeld "Optionen"](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

-   **Wirkt Ändern der Zuordnung den Code sich?**

     Ändern der Zuordnung wirkt sich nicht auf den Code in keiner Weise aus. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.

-   **Was bedeutet diese Meldung: "das Diagramm basiert möglicherweise auf einer älteren Version des Codes"?**

     Der Code wurde möglicherweise geändert, nachdem Sie die Zuordnung zuletzt aktualisiert haben. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.

-   **Wie steuere ich das Layout der Zuordnung?**

     Öffnen der **Layout** im Menü auf der zuordnungssymbolleiste:

    -   Ändern Sie das Standardlayout.

    -   Deaktivieren Sie zum Beenden an, dass die Zuordnung automatisch neu angeordnet, **Automatisches Layout beim Debugging**.

    -   Um die Zuordnung so wenig wie möglich zu ändern, wenn Sie Elemente hinzufügen, deaktivieren Sie **inkrementelles Layout**.

-   **Kann ich die Zuordnung für andere Benutzer freigeben?**

     Sie können die Zuordnung exportieren, an andere Benutzer senden (sofern Sie über Microsoft Outlook verfügen) oder in der Projektmappe speichern, um sie in der Team Foundation-Versionskontrolle einzuchecken.

     ![Freigabe Aufruflisten-Code Map für andere Benutzer](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")

-   **Wie verhindere ich die Zuordnung neue Aufruflisten automatisch hinzufügt?**

     Wählen Sie ![Schaltfläche &#45; anzeigen Aufrufliste auf Code Map automatisch](../debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") auf der Symbolleiste der Map. Um die aktuelle Aufrufliste manuell zur Karte hinzufügen möchten, drücken Sie die **STRG** + **UMSCHALT** + **`**.

     Die Zuordnung weiterhin vorhandene Aufruflisten in der Karte hervorgehoben, während des Debuggens.

-   **Was bedeuten die Elementsymbole und Pfeile?**

     Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo des jeweiligen Elements. Sie können außerdem sehen Sie sich die **Legende** um zu erfahren, was bedeutet, dass jedes Symbol.

     ![Was bedeuten die Symbole auf der Aufruflisten-Code Map? ] (../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")

 Thema

-   [Zuordnen der Aufrufliste](#MapStack)

-   [Aufzeichnen von Notizen zum code](#MakeNotes)

-   [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap)

-   [Hinzufügen von zugehörigem Code zur Zuordnung](#AddRelatedCode)

-   [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs)

## <a name="see-also"></a>Siehe auch
 [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md) [Verwenden von Code maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md) [suchen potenzieller Probleme, die mithilfe von Code zuordnen Analysen](../modeling/find-potential-problems-using-code-map-analyzers.md) [durchsuchen und Neuanordnen code Maps](../modeling/browse-and-rearrange-code-maps.md)