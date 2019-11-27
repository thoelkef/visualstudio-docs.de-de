---
title: Zuordnen von Methoden in der Aufrufliste beim Debuggen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 43
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3ddf45a48f6b9d8a5ac8155012f168703c67aa3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300780"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Zuordnen von Methoden in der Aufrufliste beim Debuggen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellen Sie eine Codezuordnung, um die Aufrufliste während des Debuggens visuell zu verfolgen. Sie können Notizen auf der Zuordnung vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.

 ![Debuggen mit Aufruf Listen in Code Maps](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Sie benötigen Folgendes:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Code, den Sie debuggen können, wie Visual C# .NET, Visual Basic .NET., C++, JavaScript oder X++

  Weitere Informationen finden Sie unter: [Video: visuelles Debuggen mit der Code Map-debuggerintegration (Channel 9)](https://go.microsoft.com/fwlink/?LinkId=293418) • zuordnen [der Rückruf Stapel](#MapStack) • [Erstellen von Notizen zum Code](#MakeNotes) • [Aktualisieren der Zuordnung mit der nächsten aufrufsstapel](#UpdateMap) • [Hinzufügen von zugehöriger Code zur](#AddRelatedCode) Zuordnung • [Suchen von Fehlern mithilfe der](#FindBugs) Zuordnung • [Q & A](#QA)

  Ausführliche Informationen zu den Befehlen und Aktionen, die Sie beim Arbeiten mit Code Maps verwenden können, finden Sie unter [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Abbilden der Aufrufliste

1. Beginnen Sie mit dem Debuggen. (Tastatur: **F5**)

2. Nachdem Ihre APP in den Unterbrechungs Modus wechselt oder Sie eine Funktion schrittweise ausführen, wählen Sie **Code Map**aus. (Tastatur: **STRG** + **UMSCHALT** +  **`** )

     ![Code Map auswählen, um die Zuordnung der aufrufsstapel](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:

     ![Weitere Informationen finden Sie unter Code Map](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Die Map wird beim Debuggen automatisch aktualisiert. Weitere Informationen finden Sie unter [Aktualisieren der Zuordnung mit der nächsten-Rückruf Stapel](#UpdateMap).

## <a name="MakeNotes"></a> Erstellen von Notizen zum Code
 Fügen Sie Kommentare hinzu, um nachzuverfolgen, was im Code geschieht. Um eine neue Zeile in einem Kommentar hinzuzufügen, drücken Sie **UMSCHALT + Return**.

 ![Kommentar zur aufrufsstapel auf Code Map hinzufügen](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Aktualisieren der Code Map mit der nächsten Aufrufliste
 Führen Sie die Anwendung bis zum nächsten Haltepunkt aus, oder führen Sie eine Funktion schrittweise aus. Die Zuordnung fügt eine neue Aufrufliste hinzu.

 ![Code Map mit nächster aufrufsstapel aktualisieren](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Code Map
 Nun verfügen Sie über eine Zuordnung. Was geschieht als Nächstes? Wenn Sie Visual C# .NET oder Visual Basic .NET. verwenden, fügen Sie Elemente wie Felder, Eigenschaften und andere Methoden hinzu, um nachzuverfolgen, was im Code geschieht.

 Doppelklicken Sie auf eine Methode, um ihre Codedefinition anzuzeigen, oder verwenden Sie das Kontextmenü für die Methode. (Tastatur: Wählen Sie die Methode auf der Karte aus, und drücken Sie **F12**.)

 ![Wechseln Sie zur Code Definition für eine Methode auf Code Map](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Fügen Sie die Elemente hinzu, die Sie in der Zuordnung nachverfolgen möchten.

 ![Felder in einer Methode in der Code Map der anzeigen](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. Dies ist zwar hilfreich, Sie können die Zuordnung jedoch auch einfach halten, indem Sie diese Funktion mithilfe der Schaltfläche übergeordnete Elemente **einschließen** auf der Kartensymbol Leiste oder durch Drücken von **STRG** beim Hinzufügen von Elementen deaktivieren.

 ![Felder, die mit einer Methode in der Code Map der](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Hier können Sie leicht erkennen, welche Methoden die gleichen Felder verwenden. Die zuletzt hinzugefügten Elemente werden grün dargestellt.

 Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.

 ![Weitere Informationen finden Sie unter Methoden, die ein Feld verwenden: Code Map der](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Methoden, die ein Feld in der aufrufsstapel Code map verwenden](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Suchen von Fehlern mithilfe der Code Map
 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Angenommen Sie untersuchen beispielsweise einen Fehler in einem Zeichenprogramm. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.

 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:

 ![Hinzufügen einer weiteren aufrufsstapel zu Code Map](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.

 Nachdem Sie den Fehler korrigiert haben und die Ausführung des Programms fortsetzen, fügt die Zuordnung den neuen Aufruf von `undo` zur `Repaint`-Funktion hinzu:

 ![Neuen Methodenaufrufe für die aufrufsstapel Code Map hinzufügen](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> Fragen und Antworten

- **Nicht alle Aufrufe werden auf der Karte angezeigt. Dafür?**

   Standardmäßig wird nur Ihr eigener Code in der Zuordnung angezeigt. Um externen Code anzuzeigen, aktivieren Sie ihn im Fenster " **aufrufsstapel** ":

   ![Anzeigen von externem Code mithilfe des Fensters "Fenster" aufrufen](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   oder deaktivieren Sie **nur eigenen Code** in den Visual Studio-Debugoptionen:

   ![Externen Code mithilfe des Dialog Felds "Optionen" anzeigen](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Wirkt sich das Ändern der Zuordnung auf den Code aus?**

   Der Code wird durch Ändern der Zuordnung in keiner Weise beeinflusst. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.

- **Was bedeutet diese Meldung: "das Diagramm basiert möglicherweise auf einer älteren Version des Codes"?**

   Der Code wurde möglicherweise geändert, nachdem Sie die Zuordnung zuletzt aktualisiert haben. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.

- **Gewusst wie das Layout der Karte Steuern?**

   Öffnen Sie das **Layoutmenü** auf der Kartensymbol Leiste:

  - Ändern Sie das Standardlayout.

  - Wenn Sie das erneute Anordnen der Zuordnung beenden möchten, deaktivieren Sie das **automatische Layout beim Debuggen**.

  - Deaktivieren Sie das **inkrementelle Layout**, um die Zuordnung so wenig wie möglich neu anzuordnen, wenn Sie Elemente hinzufügen.

- **Kann ich die Zuordnung für andere freigeben?**

   Sie können die Zuordnung exportieren, an andere Benutzer senden (sofern Sie über Microsoft Outlook verfügen) oder in der Projektmappe speichern, um sie in der Team Foundation-Versionskontrolle einzuchecken.

   ![Aufrufsstapel Code Map für andere freigeben](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Gewusst wie das Hinzufügen neuer Aufruf Listen durch die Zuordnung nicht mehr automatisch?**

   Wählen Sie auf der Symbolleiste der Symbolleiste die ![Schaltfläche &#45; Aufrufstapel auf Code Map anzeigen](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") . Wenn Sie die aktuelle aufrufsstapel der Zuordnung manuell hinzufügen möchten, drücken Sie **STRG** + **UMSCHALT** +  **`** .

   Während des Debuggens hebt die Zuordnung weiterhin vorhandene Aufruflisten in der Zuordnung hervor.

- **Was bedeuten die Symbol Symbole und Pfeile?**

   Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo für das Element an. Sie können sich auch die **Legende** ansehen, um zu erfahren, was die einzelnen Symbole bedeuten.

   ![Was bedeuten die Symbole in der aufrufsstapel Code Map?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Weitere Informationen finden Sie unter: zuordnen [der aufrufsstapel](#MapStack) • [Notizen zum Code machen](#MakeNotes) • [Aktualisieren der Zuordnung mit der nächsten Telefon Stapel](#UpdateMap) • [Hinzufügen von zugehöriger Code zur](#AddRelatedCode) Zuordnung • [Suchen von Fehlern mithilfe der](#FindBugs) Zuordnung

## <a name="see-also"></a>Siehe auch
 Zuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md) [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md) [Ermitteln potenzieller Probleme mithilfe von Code Map](../modeling/find-potential-problems-using-code-map-analyzers.md) Analyzer [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
