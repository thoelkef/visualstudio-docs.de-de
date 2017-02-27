---
title: "Zuordnen von Methoden in der Aufrufliste beim Debuggen in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.progression.debugwithcodemaps"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Aufruflistenfenster, Zuordnen von Aufrufen"
  - "Aufruflistenfenster, In der Codezuordnung zeigen"
  - "Aufruflistenfenster, Visuelles Verfolgen von Aufrufen"
  - "Aufruflistenfenster, Visuell darstellen"
  - "Aufruflisten, Codeübersichten"
  - "Aufruflisten, Zuordnen"
  - "Aufruflisten, Visuell darstellen"
  - "Debuggen [Visual Studio], Diagrammerstellung für die Aufrufliste"
  - "Debuggen [Visual Studio], Zuordnen der Aufrufliste"
  - "Debuggen [Visual Studio], Visuelles Verfolgen der Aufrufliste"
  - "Debuggen [Visual Studio], Visualisieren der Aufrufliste"
  - "Visuelles Debuggen von Code"
  - "Debuggen, Codeübersichten"
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 39
author: "mikejo5000"
ms.author: "mikejo"
manager: "douge"
caps.handback.revision: 39
---
# Zuordnen von Methoden in der Aufrufliste beim Debuggen in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellen Sie eine Codezuordnung, um die Aufrufliste während des Debuggens visuell zu verfolgen.  Sie können Notizen auf der Zuordnung vermerken, um das Verhalten des Codes zu verfolgen, sodass Sie sich auf das Suchen von Fehlern konzentrieren können.  
  
 ![Debuggen mit Aufruflisten in Codezuordnungen](../debugger/media/debuggermap_overview.png "DebuggerMap\_Overview")  
  
 Sie benötigen Folgendes:  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   Code, den Sie debuggen können, wie Visual C\# .NET, Visual Basic .NET., C\+\+, JavaScript oder X\+\+  
  
 Weitere Informationen erhalten Sie unter: [Video: Visuelles Debuggen mit der Code Map\-Debuggerintegration \(Channel 9\)](http://go.microsoft.com/fwlink/?LinkId=293418) • [Zuordnen der Aufrufliste](#MapStack) • [Aufzeichnen von Notizen zum Code](#MakeNotes) • [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap) • [Hinzufügen von zugehörigem Code zur Zuordnung](#AddRelatedCode) • [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs) • [Fragen und Antworten](#QA)  
  
 Nähere Informationen zu den Befehlen und Aktionen, die Sie bei der Arbeit mit  Codezuordnungen verwenden können, finden Sie unter [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md).  
  
##  <a name="MapStack"></a> Zuordnen der Aufrufliste  
  
1.  Beginnen Sie mit dem Debuggen.  \(Tastatur: **F5**\)  
  
2.  Wenn Ihre Anwendung in den Unterbrechungsmodus wechselt oder Sie eine Funktion schrittweise ausführen, wählen Sie **Code Map** aus.  \(Tastatur: **STRG** \+ **UMSCHALT** \+ **\`**\)  
  
     ![Codezuordnung auswählen, um Aufruflistenzuordnung zu starten](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap\_ChooseCodeMap")  
  
     Die aktuelle Aufrufliste wird in einer neuen Codezuordnung orange dargestellt:  
  
     ![Aufrufliste in Codezuordnung](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap\_SeeUndoCallStack")  
  
     Die Map wird beim Debuggen automatisch aktualisiert.  Weitere Informationen erhalten Sie unter [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap).  
  
##  <a name="MakeNotes"></a> Aufzeichnen von Notizen zum Code  
 Fügen Sie Kommentare hinzu, um nachzuverfolgen, was im Code geschieht.  Um eine neue Zeile in einem Kommentar hinzuzufügen, drücken Sie **UMSCHALT \+ EINGABE**.  
  
 ![Kommentar zu Aufrufliste in Codezuordnung hinzufügen](../debugger/media/debuggermap_addcomment.png "DebuggerMap\_AddComment")  
  
##  <a name="UpdateMap"></a> Aktualisieren der Zuordnung mit der nächsten Aufrufliste  
 Führen Sie die Anwendung bis zum nächsten Haltepunkt aus, oder führen Sie eine Funktion schrittweise aus.  Die Zuordnung fügt eine neue Aufrufliste hinzu.  
  
 ![Codezuordnung mit nächster Aufrufliste aktualisieren](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap\_AddClearCallStack")  
  
##  <a name="AddRelatedCode"></a> Hinzufügen von zugehörigem Code zur Zuordnung  
 Nun verfügen Sie über eine Zuordnung. Was geschieht als Nächstes?  Wenn Sie Visual C\# .NET oder Visual Basic .NET. verwenden, fügen Sie Elemente wie Felder, Eigenschaften und andere Methoden hinzu, um nachzuverfolgen, was im Code geschieht.  
  
 Doppelklicken Sie auf eine Methode, um ihre Codedefinition anzuzeigen, oder verwenden Sie das Kontextmenü für die Methode.  \(Tastatur: Wählen Sie die Methode in der Zuordnung aus, und drücken Sie **F12**.\)  
  
 ![Für eine Methode in der Codezuordnung zur Codedefinition wechseln](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap\_GoToCodeDefinition")  
  
 Fügen Sie die Elemente hinzu, die Sie in der Zuordnung nachverfolgen möchten.  
  
 ![Felder anzeigen, die mit einer Methode in der Aufruflisten&#45;Codezuordnung verknüpft sind](../debugger/media/debuggermap_showfields.png "DebuggerMap\_ShowFields")  
  
> [!NOTE]
>  Standardmäßig werden beim Hinzufügen von Elementen zur Zuordnung auch die übergeordnete Gruppenknoten, wie Klasse, Namespace und Assembly, hinzugefügt.  Dies ist zwar hilfreich, Sie  können die Zuordnung jedoch auch einfach halten, indem Sie diese Funktion mit dem Symbol **Übergeordnete aufnehmen** in der Zuordnungssymbolleiste, oder durch Drücken der Taste **STRG** beim Hinzufügen von Elementen deaktivieren.  
  
 ![Felder, die mit einer Methode in der Aufruflisten&#45;Codezuordnung verknüpft sind](../debugger/media/debuggermap_showedfields.png "DebuggerMap\_ShowedFields")  
  
 Hier können Sie leicht erkennen, welche Methoden die gleichen Felder verwenden.  Die zuletzt hinzugefügten Elemente werden grün dargestellt.  
  
 Setzen Sie das Erstellen der Zuordnung fort, um weiteren Code anzuzeigen.  
  
 ![Methoden, die ein Feld verwenden: Aufruflisten&#45;Codezuordnung](../debugger/media/debuggermap_findallreferences.png "DebuggerMap\_FindAllReferences")  
  
 ![Methoden, die ein Feld für die Aufruflisten&#45;Codezuordnung verwenden](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap\_FoundAllReferences")  
  
##  <a name="FindBugs"></a> Suchen von Fehlern mithilfe der Zuordnung  
 Durch die Visualisierung des Codes können Sie Fehler schneller finden.  Angenommen Sie untersuchen beispielsweise einen Fehler in einem Zeichenprogramm.  Wenn Sie eine Linie zeichnen und versuchen, sie rückgängig zu machen, geschieht nichts, bis Sie eine andere Zeile zeichnen.  
  
 Legen Sie die Haltepunkte `clear`, `undo` und `Repaint` fest, starten Sie das Debugging, und erstellen Sie eine Zuordnung wie die folgende:  
  
 ![Weitere Aufrufliste zu Codezuordnung hinzufügen](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap\_AddPaintObjectCallStack")  
  
 Sie stellen fest, dass alle Benutzergesten in der Zuordnung die `Repaint`\-Funktion aufrufen, außer `undo`.  Dies erklärt möglicherweise, warum `undo` nicht sofort funktioniert.  
  
 Nachdem Sie den Fehler korrigiert haben und die Ausführung des Programms fortsetzen, fügt die Zuordnung den neuen Aufruf von `undo` zur `Repaint`\-Funktion hinzu:  
  
 ![Neuen Methodenaufruf zu Aufrufliste in Codezuordnung hinzufügen](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap\_AddNewCallForRepaint")  
  
##  <a name="QA"></a> Fragen und Antworten  
  
-   **Nicht alle Aufrufe werden in der Zuordnung angezeigt.  Warum?**  
  
     Standardmäßig wird nur Ihr eigener Code in der Zuordnung angezeigt.  Um externen Code anzuzeigen, aktivieren Sie die entsprechende Option im Fenster **Aufrufliste**:  
  
     ![Anzeige von externem Code über das Fenster "Aufrufliste"](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap\_CallStackMenu")  
  
     oder deaktivieren Sie **Nur meinen Code aktivieren** in den Debugoptionen von Visual Studio:  
  
     ![Anzeige von externem Code über das Dialogfeld "Optionen"](../debugger/media/debuggermap_debugoptions.png "DebuggerMap\_DebugOptions")  
  
-   **Wird der Code durch Ändern der Zuordnung beeinflusst?**  
  
     Der Code wird durch Ändern der Zuordnung in keiner Weise beeinflusst.  Sie können beliebigen Code in der Zuordnung gerne umbenennen, verschieben oder entfernen.  
  
-   **Was bedeutet diese Meldung: "Das Diagramm basiert möglicherweise auf einer älteren Version des Codes"?**  
  
     Der Code wurde möglicherweise geändert, nachdem Sie die Zuordnung zuletzt aktualisiert haben.  Zum Beispiel befindet sich möglicherweise ein Aufruf für die Zuordnung nicht mehr im Code.  Schließen Sie die Meldung, und versuchen Sie dann, die Projektmappe vor der erneuten Aktualisierung der Zuordnung neu zu erstellen.  
  
-   **Wie lege ich das Layout der Zuordnung fest?**  
  
     Öffnen Sie das Menü **Layout** auf der Zuordnungssymbolleiste:  
  
    -   Ändern Sie das Standardlayout.  
  
    -   Um zu verhindern, dass die Zuordnung automatisch neu angeordnet wird, deaktivieren Sie die Option **Automatisches Layout beim Debugging**.  
  
    -   Um die Zuordnung beim Hinzufügen von Elementen so wenig wie möglich neu anzuordnen, deaktivieren Sie die Option **Inkrementelles Layout**.  
  
-   **Kann ich die Zuordnung für andere Benutzer freigeben?**  
  
     Sie können die Zuordnung exportieren, an andere Benutzer senden \(sofern Sie über Microsoft Outlook verfügen\) oder in der Projektmappe speichern, um sie in der Team Foundation\-Versionskontrolle einzuchecken.  
  
     ![Aufruflisten&#45;Codezuordnung für andere Benutzer freigeben](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap\_ShareWithOthers")  
  
-   **Wie kann ich verhindern, dass die Zuordnung neue Aufruflisten automatisch hinzufügt?**  
  
     Wählen Sie ![Schaltfläche für die automatische Anzeige der Aufrufliste in der Codezuordnung](../debugger/media/debuggermap_automaticupdateicon.png "DebuggerMap\_AutomaticUpdateIcon") in der Zuordnungssymbolleiste aus.  Um der Zuordnung die aktuelle Aufrufliste manuell hinzuzufügen, drücken Sie **STRG** \+ **UMSCHALT** \+ **\`**.  
  
     Während des Debuggens hebt die Zuordnung weiterhin vorhandene Aufruflisten in der Zuordnung hervor.  
  
-   **Was bedeuten die Elementsymbole und Pfeile?**  
  
     Um weitere Informationen zu einem Element zu erhalten, bewegen Sie den Mauszeiger darüber, und sehen Sie sich die QuickInfo für das Element an.  Sie können sich auch die **Legende** anschauen, um mehr über die Bedeutung des jeweiligen Symbols zu erfahren.  
  
     ![Was bedeuten die Symbole in der Aufruflisten&#45;Codezuordnung?](../debugger/media/debuggermap_showlegend.png "DebuggerMap\_ShowLegend")  
  
 Weitere Informationen finden Sie unter: [Zuordnen der Aufrufliste](#MapStack) • [Aufzeichnen von Notizen zum Code](#MakeNotes) • [Aktualisieren der Zuordnung mit der nächsten Aufrufliste](#UpdateMap) • [Hinzufügen von zugehörigem Code zur Zuordnung](#AddRelatedCode) • [Suchen von Fehlern mithilfe der Zuordnung](#FindBugs)  
  
## Siehe auch  
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)   
 [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Ermitteln potenzieller Probleme mithilfe von Code Map\-Analyzern](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md)