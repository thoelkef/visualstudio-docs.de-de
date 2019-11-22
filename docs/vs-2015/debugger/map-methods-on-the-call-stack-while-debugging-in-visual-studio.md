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

 ![Debugging with call stacks on code maps](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Sie benötigen Folgendes:

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- Code, den Sie debuggen können, wie Visual C# .NET, Visual Basic .NET., C++, JavaScript oder X++

  See: [Video: Debug visually with Code Map debugger integration (Channel 9)](https://go.microsoft.com/fwlink/?LinkId=293418) • [Map the call stack](#MapStack) • [Make notes about the code](#MakeNotes) • [Update the map with the next call stack](#UpdateMap) • [Add related code to the map](#AddRelatedCode) • [Find bugs using the map](#FindBugs) • [Q & A](#QA)

  For details of the commands and actions you can use when working with code maps, see [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Abbilden der Aufrufliste

1. Beginnen Sie mit dem Debuggen. (Keyboard: **F5**)

2. After your app enters break mode or you step into a function, choose **Code Map**. (Keyboard: **Ctrl** + **Shift** +  **`** )

     ![Choose Code Map to start mapping call stack](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:

     ![See call stack on code map](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     Die Map wird beim Debuggen automatisch aktualisiert. See [Update the map with the next call stack](#UpdateMap).

## <a name="MakeNotes"></a> Erstellen von Notizen zum Code
 Fügen Sie Kommentare hinzu, um nachzuverfolgen, was im Code geschieht. To add a new line in a comment, press **Shift + Return**.

 ![Add comment to call stack on code map](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Aktualisieren der Code Map mit der nächsten Aufrufliste
 Führen Sie die Anwendung bis zum nächsten Haltepunkt aus, oder führen Sie eine Funktion schrittweise aus. Die Zuordnung fügt eine neue Aufrufliste hinzu.

 ![Update code map with next call stack](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Code Map
 Nun verfügen Sie über eine Zuordnung. Was geschieht als Nächstes? Wenn Sie Visual C# .NET oder Visual Basic .NET. verwenden, fügen Sie Elemente wie Felder, Eigenschaften und andere Methoden hinzu, um nachzuverfolgen, was im Code geschieht.

 Doppelklicken Sie auf eine Methode, um ihre Codedefinition anzuzeigen, oder verwenden Sie das Kontextmenü für die Methode. (Keyboard: Select the method on the map and press **F12**)

 ![Go to code definition for a method on code map](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Fügen Sie die Elemente hinzu, die Sie in der Zuordnung nachverfolgen möchten.

 ![Show fields in a method on call stack code map](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. While this is useful, you can keep the map simple by turning off this feature using the **Include Parents** button on the map toolbar, or by pressing **CTRL** when you add items.

 ![Fields related to a method on call stack code map](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Hier können Sie leicht erkennen, welche Methoden die gleichen Felder verwenden. Die zuletzt hinzugefügten Elemente werden grün dargestellt.

 Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.

 ![See methods that use a field: call stack code map](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Methods that use a field on call stack code map](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Suchen von Fehlern mithilfe der Code Map
 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Angenommen Sie untersuchen beispielsweise einen Fehler in einem Zeichenprogramm. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.

 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:

 ![Add another call stack to code map](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.

 Nachdem Sie den Fehler korrigiert haben und die Ausführung des Programms fortsetzen, fügt die Zuordnung den neuen Aufruf von `undo` zur `Repaint`-Funktion hinzu:

 ![Add new method call to call stack on code map](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> Fragen und Antworten

- **Not all calls appear on the map. Why?**

   Standardmäßig wird nur Ihr eigener Code in der Zuordnung angezeigt. To see external code, turn it on in the **Call Stack** window:

   ![Display external code using the Call Stack window](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   or turn off **Enable Just My Code** in the Visual Studio debugging options:

   ![Show external code using Options dialog](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Does changing the map affect the code?**

   Der Code wird durch Ändern der Zuordnung in keiner Weise beeinflusst. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.

- **What does this message mean: “The diagram may be based on an older version of the code”?**

   Der Code wurde möglicherweise geändert, nachdem Sie die Zuordnung zuletzt aktualisiert haben. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.

- **How do I control the map’s layout?**

   Open the **Layout** menu on the map toolbar:

  - Ändern Sie das Standardlayout.

  - To stop rearranging the map automatically, turn off **Automatically Layout when Debugging**.

  - To rearrange the map as little as possible when you add items, turn off **Incremental Layout**.

- **Can I share the map with others?**

   Sie können die Zuordnung exportieren, an andere Benutzer senden (sofern Sie über Microsoft Outlook verfügen) oder in der Projektmappe speichern, um sie in der Team Foundation-Versionskontrolle einzuchecken.

   ![Share call stack code map with others](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **How do I stop the map from adding new call stacks automatically?**

   Choose ![Button &#45; Show call stack on code map automatically](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") on the map toolbar. To manually add the current call stack to the map, press **Ctrl** + **Shift** +  **`** .

   Während des Debuggens hebt die Zuordnung weiterhin vorhandene Aufruflisten in der Zuordnung hervor.

- **What do the item icons and arrows mean?**

   Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo für das Element an. You can also look at the **Legend** to learn what each icon means.

   ![What do icons on the call stack code map mean?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  See: [Map the call stack](#MapStack) • [Make notes about the code](#MakeNotes) • [Update the map with the next call stack](#UpdateMap) • [Add related code to the map](#AddRelatedCode) • [Find bugs using the map](#FindBugs)

## <a name="see-also"></a>Siehe auch
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md) [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md) [Find potential problems using code map analyzers](../modeling/find-potential-problems-using-code-map-analyzers.md) [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md)
