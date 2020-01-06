---
title: Zuordnen von Methoden in der Aufrufliste beim Debuggen
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a918cc94cd242c74b672ff65c3d5093f111a25f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593303"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Zuordnen von Methoden in der Aufrufliste beim Debuggen in Visual Studio

Erstellen Sie eine Code Map, um die Aufrufliste während des Debuggens visuell zu verfolgen. Sie können Notizen auf der Zuordnung vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.

 ![Debuggen mit Aufruflisten in Codezuordnungen](../debugger/media/debuggermap_overview.png)

 Sie benötigen Folgendes:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Code, den Sie, z. B. Visual c#, Visual Basic, C++, JavaScript oder X++ Debuggen können

  Thema

- [Video: Debuggen Sie visuelles mit der Code Map-debuggerintegration (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [Zuordnen der Aufrufliste](#MapStack)

- [Aufzeichnen von Notizen zum code](#MakeNotes)

- [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap)

- [Hinzufügen von zugehörigem Code zur Zuordnung](#AddRelatedCode)

- [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs)

- [HÄUFIG GESTELLTE FRAGEN](#QA)

  Details zu den Befehlen und Aktionen, die Sie bei der Arbeit mit Code Maps können, finden Sie unter [durchsuchen und Neuanordnen code Maps](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Abbilden der Aufrufliste

1. Beginnen Sie mit dem Debuggen. (Tastatur: **F5**)

2. Wählen Sie nach Ihrer app in den Unterbrechungsmodus wechselt oder Sie eine Funktion schrittweise, **Code Map**. (Tastatur: **STRG** + **UMSCHALT** +  **`** )

     ![Code Map auswählen, um Aufruflistenzuordnung zu starten](../debugger/media/debuggermap_choosecodemap.png)

     Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:

     ![Aufrufliste in Code Maps](../debugger/media/debuggermap_seeundocallstack.png)

     Die Map wird beim Debuggen automatisch aktualisiert. Finden Sie unter [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap).

## <a name="MakeNotes"></a> Erstellen von Notizen zum Code

 Fügen Sie Kommentare, um nachzuverfolgen, was im Code geschieht. Um eine neue Zeile in einem Kommentar hinzuzufügen, drücken Sie die **Umschalt + Eingabe**.

 ![Kommentar zu Aufrufliste in Code Map hinzufügen](../debugger/media/debuggermap_addcomment.png)

## <a name="UpdateMap"></a> Aktualisieren der Code Map mit der nächsten Aufrufliste

 Führen Sie die Anwendung bis zum nächsten Haltepunkt aus, oder führen Sie eine Funktion schrittweise aus. Die Zuordnung fügt eine neue Aufrufliste hinzu.

 ![Code Map mit nächster Aufrufliste aktualisieren](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Code Map

 Jetzt haben Sie einer Karte – was geschieht als Nächstes? Wenn Sie mit c# oder Visual Basic arbeiten, fügen Sie Elemente wie Felder, Eigenschaften und andere Methoden, um nachzuverfolgen, was im Code geschieht.

 Doppelklicken Sie auf eine Methode, um ihre Codedefinition anzuzeigen, oder verwenden Sie das Kontextmenü für die Methode. (Tastatur: Wählen Sie die Methode auf der Karte, und drücken Sie **F12**)

 ![Für eine Methode in der Codezuordnung zur Codedefinition wechseln](../debugger/media/debuggermap_gotocodedefinition.png)

 Fügen Sie die Elemente hinzu, die Sie in der Zuordnung nachverfolgen möchten.

 ![Felder anzeigen, die mit einer Methode in der Aufruflisten-Codezuordnung verknüpft sind](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. Dies ist, zwar hilfreich Sie können einfach halten, die Zuordnung durch Deaktivieren dieser Funktion mit dem **übergeordnete Elemente einschließen** Schaltfläche auf der Symbolleiste der Map oder durch Drücken von **STRG** beim Hinzufügen von Elementen.

 ![Felder, die mit einer Methode in der Aufruflisten-Codezuordnung verknüpft sind](../debugger/media/debuggermap_showedfields.png)

 Hier können Sie leicht erkennen, welche Methoden die gleichen Felder verwenden. Die zuletzt hinzugefügten Elemente werden grün dargestellt.

 Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.

 ![Methoden, die ein Feld verwenden: Aufruflisten-Code Map](../debugger/media/debuggermap_findallreferences.png)

 ![Methoden, die ein Feld für die Aufruflisten-Code Maps verwenden](../debugger/media/debuggermap_foundallreferences.png)

## <a name="FindBugs"></a> Suchen von Fehlern mithilfe der Code Map

 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Nehmen wir beispielsweise an, dass Sie einen Fehler in einem Zeichenprogramm untersuchen. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.

 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:

 ![Weitere Aufrufliste zu Codezuordnung hinzufügen](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.

 Nachdem Sie den Fehler korrigiert haben und die Ausführung des Programms fortsetzen, fügt die Zuordnung den neuen Aufruf von `undo` zur `Repaint`-Funktion hinzu:

 ![Neuen Methodenaufruf zu Aufrufliste in Code Maps hinzufügen](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="QA"></a> Fragen und Antworten

- **Nicht alle Aufrufe werden auf der Karte angezeigt. Dafür?**

   Standardmäßig wird nur Ihr eigener Code in der Zuordnung angezeigt. Um externen Code anzuzeigen, aktivieren Sie ihn im der **Aufrufliste** Fenster:

   ![Anzeige von externem Code über das Fenster "Aufrufliste"](../debugger/media/debuggermap_callstackmenu.png)

   oder deaktivieren Sie **nur meinen Code aktivieren** im Visual Studio-Debugoptionen:

   ![Anzeige von externem Code über das Dialogfeld "Optionen"](../debugger/media/debuggermap_debugoptions.png)

- **Wirkt Ändern der Zuordnung den Code sich?**

   Ändern der Zuordnung wirkt sich nicht auf den Code in keiner Weise aus. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.

- **Was bedeutet diese Meldung: "das Diagramm basiert möglicherweise auf einer älteren Version des Codes"?**

   Der Code wurde möglicherweise geändert, nachdem Sie die Zuordnung zuletzt aktualisiert haben. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.

- **Wie steuere ich das Layout der Zuordnung?**

   Öffnen der **Layout** im Menü auf der zuordnungssymbolleiste:

  - Ändern Sie das Standardlayout.

  - Deaktivieren Sie zum Beenden an, dass die Zuordnung automatisch neu angeordnet, **Automatisches Layout beim Debugging**.

  - Um die Zuordnung so wenig wie möglich zu ändern, wenn Sie Elemente hinzufügen, deaktivieren Sie **inkrementelles Layout**.

- **Kann ich die Zuordnung für andere Benutzer freigeben?**

   Sie können Exportieren der Code Map, die an andere Personen zu senden, wenn Sie Microsoft Outlook oder speichern Sie sie der Projektmappe aus, damit Sie ihn in die quellcodeverwaltung einchecken können.

   ![Aufruflisten-Code Map für andere Benutzer freigeben](../debugger/media/debuggermap_sharewithothers.png)

- **Wie verhindere ich die Zuordnung neue Aufruflisten automatisch hinzufügt?**

   Wählen Sie ![Schaltfläche &#45; anzeigen Aufrufliste auf Code Map automatisch](../debugger/media/debuggermap_automaticupdateicon.gif) auf der Symbolleiste der Map. Um die aktuelle Aufrufliste manuell zur Karte hinzufügen möchten, drücken Sie die **STRG** + **UMSCHALT** +  **`** .

   Die Zuordnung weiterhin vorhandene Aufruflisten in der Karte hervorgehoben, während des Debuggens.

- **Was bedeuten die Elementsymbole und Pfeile?**

   Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo des jeweiligen Elements. Sie können außerdem sehen Sie sich die **Legende** um zu erfahren, was bedeutet, dass jedes Symbol.

   ![Was bedeuten die Symbole in der Aufruflisten-Codezuordnung?](../debugger/media/debuggermap_showlegend.png)

  Thema

- [Zuordnen der Aufrufliste](#MapStack)

- [Aufzeichnen von Notizen zum code](#MakeNotes)

- [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap)

- [Hinzufügen von zugehörigem Code zur Zuordnung](#AddRelatedCode)

- [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs)

## <a name="see-also"></a>Siehe auch

- [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)
- [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)
- [Ermitteln potenzieller Probleme mithilfe von Code Map-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
