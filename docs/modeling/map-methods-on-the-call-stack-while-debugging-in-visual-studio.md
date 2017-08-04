---
title: Zuordnen von Methoden in der Aufrufliste beim Debuggen in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ab08446140608a65b6894b3015c52227040611fd
ms.lasthandoff: 02/22/2017

---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Zuordnen von Methoden in der Aufrufliste beim Debuggen in Visual Studio
Erstellen Sie eine Code Map, um die Aufrufliste während des Debuggens visuell zu verfolgen. Sie können Notizen auf der Zuordnung vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.  
  
 ![Debuggen mit Aufruflisten in codezuordnungen](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")  
  
 Sie benötigen Folgendes:  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   Code, den Sie debuggen können, wie Visual C# .NET, Visual Basic .NET., C++, JavaScript oder X++  
  
 Siehe: [Video: visuelles Debuggen mit Code Map-debuggerintegration (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418) • [Zuordnen der Aufrufliste](#MapStack) • [Notizen zum Code](#MakeNotes) • [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap) • [Hinzufügen von zugehörigem Code zur Zuordnung](#AddRelatedCode) • [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs) • [F & A](#QA)  
  
 Einzelheiten von Befehlen und Aktionen Sie beim Arbeiten mit Code Maps können finden Sie unter [durchsuchen und Neuanordnen code Maps](../modeling/browse-and-rearrange-code-maps.md).  
  
##  <a name="a-namemapstacka-map-the-call-stack"></a><a name="MapStack"></a>Zuordnen der Aufrufliste  
  
1.  Beginnen Sie mit dem Debuggen. (Tastatur: **F5**)  
  
2.  Wenn Ihre app in den Unterbrechungsmodus wechselt oder eine Funktion schrittweise, wählen **Codezuordnung**. (Keyboard: **Ctrl** + **Shift** + **`**)  
  
     ![Wählen Sie die Code Map, um aufruflistenzuordnung zu starten](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")  
  
     Die aktuelle Aufrufliste wird in einer neuen Code Map orange dargestellt:  
  
     ![Finden Sie in der Aufrufliste in codezuordnung](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")  
  
     Die Map wird beim Debuggen automatisch aktualisiert. Finden Sie unter [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap).  
  
##  <a name="a-namemakenotesa-make-notes-about-the-code"></a><a name="MakeNotes"></a>Aufzeichnen von Notizen Sie zum code  
 Fügen Sie Kommentare hinzu, um nachzuverfolgen, was im Code geschieht. Um eine neue Zeile in einen Kommentar hinzuzufügen, drücken Sie die **Umschalt + Eingabe**.  
  
 ![Kommentar zu Aufrufliste in codezuordnung hinzufügen](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")  
  
##  <a name="a-nameupdatemapa-update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a>Aktualisieren der Zuordnung mit der nächsten Aufrufliste  
 Führen Sie die Anwendung bis zum nächsten Haltepunkt aus, oder führen Sie eine Funktion schrittweise aus. Die Zuordnung fügt eine neue Aufrufliste hinzu.  
  
 ![Codezuordnung mit nächster Aufrufliste aktualisieren](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")  
  
##  <a name="a-nameaddrelatedcodea-add-related-code-to-the-map"></a><a name="AddRelatedCode"></a>Hinzufügen von zugehörigem Code zur Zuordnung  
 Nun verfügen Sie über eine Zuordnung. Was geschieht als Nächstes? Wenn Sie Visual C# .NET oder Visual Basic .NET. verwenden, fügen Sie Elemente wie Felder, Eigenschaften und andere Methoden hinzu, um nachzuverfolgen, was im Code geschieht.  
  
 Doppelklicken Sie auf eine Methode, um ihre Codedefinition anzuzeigen, oder verwenden Sie das Kontextmenü für die Methode. (Tastatur: Wählen Sie die Methode für die Zuordnung, und drücken Sie **F12**)  
  
 ![Wechseln Sie zum Code-Definition für eine Methode in Code Map](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")  
  
 Fügen Sie die Elemente hinzu, die Sie in der Zuordnung nachverfolgen möchten.  
  
 ![Felder anzeigen, die eine Methode in der Aufruflisten-codezuordnung](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")  
  
> [!NOTE]
>  Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt. Während dies nützlich ist, Sie können einfach halten, die Zuordnung durch das Deaktivieren dieser Funktion mit dem **übergeordnete Elemente einschließen** Schaltfläche auf der Symbolleiste der Map, oder drücken Sie **STRG** beim Hinzufügen von Elementen.  
  
 ![Felder im Zusammenhang mit einer Methode in der Aufruflisten-codezuordnung](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")  
  
 Hier können Sie leicht erkennen, welche Methoden die gleichen Felder verwenden. Die zuletzt hinzugefügten Elemente werden grün dargestellt.  
  
 Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.  
  
 ![Methoden, die ein Feld verwenden: Aufruflisten-codezuordnung](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")  
  
 ![Methoden, mit denen ein Feld auf Aufruflisten-codezuordnung](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")  
  
##  <a name="a-namefindbugsa-find-bugs-using-the-map"></a><a name="FindBugs"></a>Suchen von Fehlern mithilfe der Zuordnungs  
 Durch die Visualisierung des Codes können Sie Fehler schneller finden. Angenommen Sie untersuchen beispielsweise einen Fehler in einem Zeichenprogramm. Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.  
  
 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:  
  
 ![Weitere Aufrufliste zu codezuordnung hinzufügen](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")  
  
 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`-Funktion aufrufen, außer `undo`. Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.  
  
 Nachdem Sie den Fehler korrigiert haben und die Ausführung des Programms fortsetzen, fügt die Zuordnung den neuen Aufruf von `undo` zur `Repaint`-Funktion hinzu:  
  
 ![Neuen Methodenaufruf zu Aufrufliste in codezuordnung hinzufügen](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")  
  
##  <a name="a-nameqaa-q--a"></a><a name="QA"></a> Fragen und Antworten  
  
-   **Nicht alle Aufrufe werden auf der Karte angezeigt. Warum?**  
  
     Standardmäßig wird nur Ihr eigener Code in der Zuordnung angezeigt. Um externen Code anzuzeigen, aktivieren Sie es in der **Aufrufliste** Fenster:  
  
     ![Anzeige von externem Code über das Fenster "Aufrufliste"](~/debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")  
  
     oder deaktivieren Sie **nur meinen Code aktivieren** in Visual Studio Debuggen von Optionen:  
  
     ![Anzeigen von externem Code über das Dialogfeld "Optionen"](~/debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")  
  
-   **Wirkt Ändern der Zuordnung den Code sich?**  
  
     Der Code wird durch Ändern der Zuordnung in keiner Weise beeinflusst. Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.  
  
-   **Was bedeutet diese Meldung: "das Diagramm basiert möglicherweise auf einer älteren Version des Codes"?**  
  
     Der Code wurde möglicherweise geändert, nachdem Sie die Zuordnung zuletzt aktualisiert haben. Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code. Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.  
  
-   **Steuern das Layout der Zuordnung**  
  
     Öffnen Sie die **Layout** Menü auf der Symbolleiste der Map:  
  
    -   Ändern Sie das Standardlayout.  
  
    -   Deaktivieren Sie zum Beenden, dass die Zuordnung automatisch neu angeordnet, **Automatisches Layout beim Debugging**.  
  
    -   Um die Zuordnung so wenig wie möglich zu ändern, wenn Sie Elemente hinzufügen, deaktivieren Sie **inkrementelles Layout**.  
  
-   **Kann ich die Zuordnung für andere Benutzer freigeben?**  
  
     Sie können die Zuordnung exportieren, an andere Benutzer senden (sofern Sie über Microsoft Outlook verfügen) oder in der Projektmappe speichern, um sie in der Team Foundation-Versionskontrolle einzuchecken.  
  
     ![Freigabe Aufruflisten-codezuordnung für andere](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")  
  
-   **Wie verhindere ich die Zuordnung neue Aufruflisten automatisch hinzufügt?**  
  
     Wählen Sie ![Schaltfläche Anzeigen der Aufrufliste in codezuordnung automatisch](~/debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") auf der Symbolleiste der Map. Um die aktuelle Aufrufliste manuell zur Karte hinzuzufügen, drücken Sie die **STRG** + **UMSCHALT** + **`**.  
  
     Während des Debuggens hebt die Zuordnung weiterhin vorhandene Aufruflisten in der Zuordnung hervor.  
  
-   **Was bedeuten die Elementsymbole und Pfeile?**  
  
     Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo für das Element an. Sie können auch hier die **Legende** um zu erfahren, was bedeutet, dass jedes Symbol.  
  
     ![Was bedeuten die Symbole auf der Aufruflisten-codezuordnung? ] (../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")  
  
 Siehe: [Zuordnen der Aufrufliste](#MapStack) • [Notizen zum Code](#MakeNotes) • [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap) • [Hinzufügen von zugehörigem Code zur Zuordnung](#AddRelatedCode) • [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs)  
  
## <a name="see-also"></a>Siehe auch  
 [Projektmappenübergreifendes Zuordnen von Abhängigkeiten](../modeling/map-dependencies-across-your-solutions.md)   
 [Verwenden von Code Maps zum Debuggen von Anwendungen](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Ermitteln Sie potenzieller Probleme mithilfe von Code Map-Analyzer](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Durchsuchen und Neuanordnen von Code Maps](../modeling/browse-and-rearrange-code-maps.md)
