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
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 414022e4e3c058826705845d57de62a9114fc821
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847524"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Zuordnen von Methoden in der Aufrufliste beim Debuggen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellen Sie eine Codezuordnung, um die Aufrufliste während des Debuggens visuell zu verfolgen. Sie können Notizen auf der Zuordnung vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.

 ![Debuggen mit Aufruflisten in Code Maps](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Sie benötigen Folgendes:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Code, den Sie debuggen können, wie Visual C# .NET, Visual Basic .NET., C++, JavaScript oder X++

  Weitere Informationen finden Sie unter: [Video: visuelles Debuggen mit der Code Map-debuggerintegration (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration) • zuordnen [der Rückruf Stapel](#MapStack) • [Erstellen von Notizen zum Code](#MakeNotes) • [Aktualisieren der Zuordnung mit der nächsten aufrufsstapel](#UpdateMap) • [Hinzufügen von zugehöriger Code zur](#AddRelatedCode) Zuordnung • [Suchen von Fehlern mithilfe der](#FindBugs) Zuordnung • [Q & A](#QA)

  Ausführliche Informationen zu den Befehlen und Aktionen, die Sie beim Arbeiten mit Code Maps verwenden können, finden Sie unter [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Abbilden der Aufrufliste

1. Beginnen Sie mit dem Debuggen. (Tastatur: **F5**)

2. Nachdem Ihre APP in den Unterbrechungs Modus wechselt oder Sie eine Funktion schrittweise ausführen, wählen Sie **Code Map**aus. (Tastatur: **STRG**  +  **UMSCHALT**  +  **`** )

     ![Code Map auswählen, um Aufruflistenzuordnung zu starten](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:

     ![Aufrufliste in Code Maps](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Die Map wird beim Debuggen automatisch aktualisiert. Weitere Informationen finden Sie unter [Aktualisieren der Zuordnung mit der nächsten-Rückruf Stapel](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Erstellen von Notizen zum Code
 Fügen Sie Kommentare hinzu, um nachzuverfolgen, was im Code geschieht. Um eine neue Zeile in einem Kommentar hinzuzufügen, drücken Sie **UMSCHALT + Return**.

 ![Kommentar zu Aufrufliste in Code Map hinzufügen](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Aktualisieren der Code Map mit der nächsten Aufrufliste
 Führen Sie die Anwendung bis zum nächsten Haltepunkt aus, oder führen Sie eine Funktion schrittweise aus. Die Zuordnung fügt eine neue Aufrufliste hinzu.

 ![Code Map mit nächster Aufrufliste aktualisieren](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Code Map
 Nun verfügen Sie über eine Zuordnung. Was geschieht als Nächstes? Wenn Sie Visual C# .NET oder Visual Basic .NET. verwenden, fügen Sie Elemente wie Felder, Eigenschaften und andere Methoden hinzu, um nachzuverfolgen, was im Code geschieht.

 Doppelklicken Sie auf eine Methode, um ihre Codedefinition anzuzeigen, oder verwenden Sie das Kontextmenü für die Methode. (Tastatur: Wählen Sie die Methode auf der Karte aus, und drücken Sie **F12**.)

 ![Für eine Methode in der Code Map zur Codedefinition wechseln](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Fügen Sie die Elemente hinzu, die Sie in der Zuordnung nachverfolgen möchten.

 ![Felder anzeigen, die mit einer Methode in der Aufruflisten-Code Map verknüpft sind](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. Dies ist zwar hilfreich, Sie können die Zuordnung jedoch auch einfach halten, indem Sie diese Funktion mithilfe der Schaltfläche übergeordnete Elemente **einschließen** auf der Kartensymbol Leiste oder durch Drücken von **STRG** beim Hinzufügen von Elementen deaktivieren.

 ![Felder, die mit einer Methode in der Aufruflisten-Code Map verknüpft sind](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Hier können Sie leicht erkennen, welche Methoden die gleichen Felder verwenden. Die zuletzt hinzugefügten Elemente werden grün dargestellt.

 Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.

 ![Methoden, die ein Feld verwenden: Aufruflisten-Code Map](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Methoden, die ein Feld für die Aufruflisten-Code Maps verwenden](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Suchen von Fehlern mithilfe der Code Map
 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Angenommen Sie untersuchen beispielsweise einen Fehler in einem Zeichenprogramm. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.

 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:

 ![Weitere Aufrufliste zu Code Map hinzufügen](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.

 Nachdem Sie den Fehler korrigiert haben und die Ausführung des Programms fortsetzen, fügt die Zuordnung den neuen Aufruf von `undo` zur `Repaint`-Funktion hinzu:

 ![Neuen Methodenaufruf zu Aufrufliste in Code Map hinzufügen](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="q--a"></a><a name="QA"></a> Fragen und Antworten

- **Nicht alle Aufrufe werden auf der Karte angezeigt. Dafür?**

   Standardmäßig wird nur Ihr eigener Code in der Code Map angezeigt. Um externen Code anzuzeigen, aktivieren Sie ihn im Fenster " **aufrufsstapel** ":

   ![Anzeige von externem Code über das Fenster „Aufrufliste“](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   oder deaktivieren Sie **nur eigenen Code** in den Visual Studio-Debugoptionen:

   ![Anzeige von externem Code über das Dialogfeld „Optionen“](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Wird der Code durch Ändern der Zuordnung beeinflusst?**

   Der Code wird durch Ändern der Zuordnung in keiner Weise beeinflusst. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.

- **Was bedeutet diese Meldung: "Das Diagramm basiert möglicherweise auf einer älteren Version des Codes"?**

   Der Code wurde möglicherweise geändert, nachdem Sie die Zuordnung zuletzt aktualisiert haben. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.

- **Wie lege ich das Layout der Zuordnung fest?**

   Öffnen Sie das **Layoutmenü** auf der Kartensymbol Leiste:

  - Ändern Sie das Standardlayout.

  - Wenn Sie das erneute Anordnen der Zuordnung beenden möchten, deaktivieren Sie das **automatische Layout beim Debuggen**.

  - Deaktivieren Sie das **inkrementelle Layout**, um die Zuordnung so wenig wie möglich neu anzuordnen, wenn Sie Elemente hinzufügen.

- **Kann ich die Zuordnung für andere Benutzer freigeben?**

   Sie können die Zuordnung exportieren, an andere Benutzer senden (sofern Sie über Microsoft Outlook verfügen) oder in der Projektmappe speichern, um sie in der Team Foundation-Versionskontrolle einzuchecken.

   ![Aufruflisten-Code Map für andere Benutzer freigeben](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Wie kann ich verhindern, dass die Zuordnung neue Aufruflisten automatisch hinzufügt?**

   Wählen Sie Schalt &#45; Fläche aus, um die Code Map in der Kartensymbol Leiste ![automatisch auf anzuzeigen](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") . Drücken Sie **STRG** + **UMSCHALT** +  **`** , um die aktuelle Aufrufliste der Code Map manuell hinzuzufügen.

   Während des Debuggens hebt die Zuordnung weiterhin vorhandene Aufruflisten in der Zuordnung hervor.

- **Was bedeuten die Elementsymbole und Pfeile?**

   Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo für das Element an. Sie können sich auch die **Legende** ansehen, um zu erfahren, was die einzelnen Symbole bedeuten.

   ![Was bedeuten die Symbole in der Aufruflisten-Codezuordnung?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Weitere Informationen finden Sie unter: zuordnen [der aufrufsstapel](#MapStack) • [Notizen zum Code machen](#MakeNotes) • [Aktualisieren der Zuordnung mit der nächsten Telefon Stapel](#UpdateMap) • [Hinzufügen von zugehöriger Code zur](#AddRelatedCode) Zuordnung • [Suchen von Fehlern mithilfe der](#FindBugs) Zuordnung

## <a name="see-also"></a>Weitere Informationen
 Zuordnen von [Abhängigkeiten in ihren Lösungen](../modeling/map-dependencies-across-your-solutions.md) [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md) [Ermitteln potenzieller Probleme mithilfe von Code Map](../modeling/find-potential-problems-using-code-map-analyzers.md) Analyzer [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
