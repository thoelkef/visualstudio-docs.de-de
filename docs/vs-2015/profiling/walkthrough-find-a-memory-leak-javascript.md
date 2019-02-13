---
title: 'Exemplarische Vorgehensweise: Suchen eines Speicherverlusts (JavaScript) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- memory leaks, JavaScript example
ms.assetid: f595412f-776b-49a2-8433-ea0062c6904d
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88f9d8fc871f182bb3a6d7f36c3648982e7a9684
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780933"
---
# <a name="walkthrough-find-a-memory-leak-javascript"></a>Exemplarische Vorgehensweise: Suchen eines Speicherverlusts (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gilt Sie für Windows und Windows Phone] (.. /Image/windows_and_phone_content.png "Windows_and_phone_content")  
  
 Diese exemplarische Vorgehensweise führt Sie durch den Prozess zum Identifizieren und Beheben eines einfachen Arbeitsspeicherproblems mithilfe der JavaScript-Speicheranalyse. Die JavaScript-Speicheranalyse ist in Visual Studio für Windows Store-Apps verfügbar, die für Windows mit JavaScript erstellt wurden. In diesem Szenario erstellen Sie eine App, die fehlerhafterweise DOM-Elemente im Speicher behält, anstatt Elemente mit derselben Geschwindigkeit zu löschen, mit der sie erstellt werden.  
  
 Obwohl die Ursache für den Speicherverlust in dieser App sehr spezifisch ist, demonstrieren die hier gezeigten Schritte einen Workflow, der normalerweise wirkungsvoll die Objekte isoliert, die den Speicherverlust verursachen.  
  
### <a name="running-the-javascript-memory-analyzer-test-app"></a>Ausführen der Test-App zur JavaScript-Speicheranalyse  
  
1.  Wählen Sie in Visual Studio **Datei**, **Neu**, **Projekt**aus.  
  
2.  Wählen Sie im linken Bereich **JavaScript** und anschließend **Windows**, **Windows 8**und dann entweder **Universell** oder **Windows Phone-Apps**aus.  
  
    > [!IMPORTANT]
    >  Die in diesem Thema gezeigten Ergebnisse der Speicherauslastung werden für eine Windows 8-App getestet.  
  
3.  Wählen Sie dann im mittleren Bereich die Projektvorlage **Leere App** aus.  
  
4.  Geben Sie im Feld **Name** einen Namen wie `JS_Mem_Tester`an, und wählen Sie dann **OK**aus.  
  
5.  Öffnen Sie im **Projektmappen-Explorer** „default.html“, und fügen Sie den folgenden Code zwischen den \<body>-Tags ein:  
  
    ```html  
    <div class="wrapper">  
        <div id="item"></div>  
        <button class="memleak" style="display: block" >Leak Memory</button>  
    </div>  
    ```  
  
    > [!IMPORTANT]
    >  Wenn Sie eine Vorlage für universelle Windows 8.1-Apps verwenden, müssen Sie HTML- und CSS-Code sowohl in den ".Windows"- als auch in den ".WindowsPhone"-Projekten aktualisieren.  
  
6.  Öffnen Sie default.css, und fügen Sie den folgenden CSS-Code hinzu:  
  
    ```css  
    .memleak {  
        position: absolute; top: 100px; left: 100px;  
    }  
    ```  
  
7.  Öffnen Sie default.js, und ersetzen Sie den gesamten Code mit dem folgenden Code:  
  
    ```javascript  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var activation = Windows.ApplicationModel.Activation;  
  
        var wrapper;  
        var elem;  
  
        app.onactivated = function (args) {  
            if (args.detail.kind === activation.ActivationKind.launch) {  
                if (args.detail.previousExecutionState !== activation.ApplicationExecutionState.terminated) {  
                } else {  
                }  
                args.setPromise(WinJS.UI.processAll());  
  
                elem = document.getElementById("item");  
                wrapper = document.querySelector(".wrapper");  
                var btn = document.querySelector(".memleak");  
                btn.addEventListener("click", btnHandler);  
                run();  
            }  
        };  
  
        app.oncheckpoint = function (args) {  
        };  
  
        app.start();  
  
        function run() {  
            initialize();  
            load();  
        }  
  
        function initialize() {  
  
            if (wrapper != null) {  
                elem.removeNode(true);  
            }  
        }  
  
        function load() {  
  
            var newDiv = document.createElement("div");  
  
            newDiv.style.zIndex = "-1";  
            newDiv.id = "item";  
  
            wrapper.appendChild(newDiv);  
        }  
  
        function btnHandler(args) {  
            run();  
        }  
  
    })();  
    ```  
  
8.  Drücken Sie die F5-TASTE, um das Debuggen zu starten. Überprüfen Sie, dass die Schaltfläche **Speicherverlust** auf der Seite angezeigt wird.  
  
9. Wechseln Sie zu Visual Studio zurück (ALT+TAB), und drücken Sie die Tastenkombination UMSCHALT+F5, um das Debugging zu beenden.  
  
     Nachdem die Funktionsweise der App sichergestellt wurde, können Sie die Speicherauslastung überprüfen.  
  
### <a name="analyzing-the-memory-usage"></a>Analysieren der Speicherauslastung  
  
1. Wählen Sie auf der Symbolleiste **Debuggen** in der Liste **Debuggen starten** das Debugziel für das aktualisierte Projekt aus, entweder die Windows Phone-Emulatoren oder den **Simulator**.  
  
   > [!TIP]
   >  Für eine Windows Store-App können Sie in dieser Liste auch **Lokaler Computer** oder **Remotecomputer** auswählen. Allerdings liegt der Vorteil des Emulators oder Simulators darin, dass Sie ihn neben Visual Studio platzieren und problemlos zwischen der laufenden App und der JavaScript-Speicheranalyse wechseln können. Weitere Informationen finden Sie unter [Ausführen von Apps aus Visual Studio](../debugger/run-store-apps-from-visual-studio.md) und [Ausführen von Windows Store-Apps auf einem Remotecomputer](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
2. Klicken Sie im Menü **Debuggen** auf **Leistungsprofiler…**.  
  
3. Wählen Sie unter **Verfügbare Tools**die Option **JavaScript-Memory**aus, und wählen Sie dann **Starten**.  
  
    In diesem Lernprogramm fügen Sie die Speicheranalyse an das Startprojekt an. Informationen zu anderen Optionen, wie das Anfügen des Arbeitsspeicheranalyzers an eine installierte App, finden Sie unter [JavaScript-Memory](../profiling/javascript-memory.md)aus.  
  
    Bei Start des Arbeitsspeicheranalyzers, wird möglicherweise eine Benutzerkontensteuerung die Berechtigung zum Ausführen der Datei "VsEtwCollector.exe" abfragen. Klicken Sie auf **Ja**.  
  
4. Wählen Sie viermal nacheinander die Schaltfläche **Speicherverlust** aus.  
  
    Bei Auswahl dieser Schaltfläche funktioniert der Ereignishandlercode in "default.js" so, dass ein Speicherverlust hervorgerufen wird. Dies wird zu Diagnosezwecken verwendet.  
  
   > [!TIP]
   >  Durch die Wiederholung des Szenarios, das Sie auf einen Speicherverlust testen möchten, wird es einfacher, irrelevante Informationen herauszufiltern. Dazu zählen beispielsweise Objekte, die dem Heap während des Startens der App oder beim Laden einer Seite hinzugefügt werden.  
  
5. Wechseln Sie aus der ausgeführten App zu Visual Studio (ALT+TAB).  
  
    Die JavaScript-Speicheranalyse zeigt Informationen auf einer neuen Registerkarte in Visual Studio an.  
  
    Das Arbeitsspeicherdiagramm in dieser Zusammenfassungsansicht veranschaulicht die Prozessspeicherauslastung im Zeitverlauf. Die Ansicht bietet auch Befehle wie **Heap-Momentaufnahme erstellen**. Eine Momentaufnahme stellt ausführliche Informationen zur Speicherauslastung zu einem bestimmten Zeitpunkt bereit. Weitere Informationen finden Sie unter [JavaScript-Memory](../profiling/javascript-memory.md)aus.  
  
6. Wählen Sie **Heap-Momentaufnahme erstellen**aus.  
  
7. Wechseln Sie zur App, und wählen Sie **Speicherverlust**aus.  
  
8. Wechseln Sie zu Visual Studio, und wählen Sie erneut **Heap-Momentaufnahme erstellen** aus.  
  
    Diese Abbildung zeigt die Baselinemomentaufnahme (Nr. 1) und die Momentaufnahme Nr. 2.  
  
    ![Baseline-Momentaufnahme und Momentaufnahme 2](../profiling/media/js-mem-app-snapshot2.png "JS_Mem_App_Snapshot2")  
  
   > [!NOTE]
   >  Der Windows Phone-Emulator zeigt keinen Screenshot von der App zum Zeitpunkt der Momentaufnahme.  
  
9. Wechseln Sie zur App, und wählen Sie die Schaltfläche **Speicherverlust** erneut aus.  
  
10. Wechseln Sie zu Visual Studio, und wählen Sie zum dritten Mal **Heap-Momentaufnahme erstellen** aus.  
  
    > [!TIP]
    >  Indem eine dritte Momentaufnahme in diesem Workflow aufgenommen wird, können Sie Änderungen zwischen der Baselinemomentaufnahme zur zweiten Momentaufnahme herausfiltern, die mit Arbeitsspeicherverlusten nichts zu tun haben. Es gibt z. B. möglicherweise erwartete Änderungen, wie Aktualisieren von Kopf- und Fußzeilen auf einer Seite, die einige Änderungen bei der Speicherauslastung generiert, aber mit Arbeitsspeicherverlusten nicht in Verbindung steht.  
  
     Diese Abbildung zeigt Momentaufnahme Nr. 2 und Momentaufnahme Nr. 3.  
  
     ![Momentaufnahme 2 und Momentaufnahme 3](../profiling/media/js-mem-app-snapshot3.png "JS_Mem_App_Snapshot3")  
  
11. Wählen Sie in Visual Studio **Beenden** aus, um die Profilerstellung zu beenden.  
  
12. Vergleichen Sie die Momentaufnahmen in Visual Studio. Momentaufnahme 2 zeigt Folgendes:  
  
    - Die Heapgröße (angezeigt durch den roten Pfeil nach oben auf der linken Seite) hat sich verglichen mit Momentaufnahme Nr. 1 um mehrere KB erhöht.  
  
      > [!IMPORTANT]
      >  Die genauen Speicherauslastungswerte für die Heapgröße hängen vom Debugziel ab.  
  
    - Die Anzahl der Objekte im Heap (angezeigt durch den roten Pfeil nach oben auf der rechten Seite) hat sich verglichen mit Momentaufnahme Nr. 1 erhöht. Ein Objekt wurde hinzugefügt (+ 1), und es wurden keine Objekte entfernt (– 0).  
  
      Momentaufnahme 3 zeigt Folgendes:  
  
    - Die Heapgröße hat sich verglichen mit Momentaufnahme Nr. 2 wieder um mehrere hundert Bytes erhöht.  
  
    - Die Anzahl der Objekte im Heap hat verglichen mit Momentaufnahme Nr. 2 wieder zugenommen. Ein Objekt wurde hinzugefügt (+ 1), und es wurden keine Objekte entfernt (– 0).  
  
13. Wählen Sie in Momentaufnahme Nr. 3 den Linktext auf der rechten Seite aus, der einen Wert von +1/-0 neben dem roten Pfeil nach oben anzeigt.  
  
     ![Link zur anderen Ansicht der Heap-Objekte](../profiling/media/js-mem-app-link.png "JS_Mem_App_Link")  
  
     Hierdurch wird die differenzielle Ansicht der Objekte im Heap mit dem Namen **Momentaufnahme #3 - Momentaufnahme #2**aufgerufen, bei der die Ansicht "Typen" standardmäßig anzeigt wird. Standardmäßig sehen Sie eine Liste von Objekten, die dem Heap zwischen Momentaufnahme Nr. 2 und Momentaufnahme Nr. 3 hinzugefügt wurden.  
  
14. Wählen Sie im Filter **Bereich** die Option **Übrige Objekte der Momentaufnahme #2**aus.  
  
15. Öffnen Sie das HTMLDivElement-Objekt oben in der Objektstruktur wie hier gezeigt.  
  
     ![Andere Ansicht der Objektanzahl auf dem Heap](../profiling/media/js-mem-app-typesdiff.png "JS_Mem_App_TypesDiff")  
  
     Diese Ansicht zeigt nützliche Informationen zum Speicherverlust, wie beispielsweise Folgende:  
  
    - Diese Ansicht zeigt ein DIV-Element mit der ID `item`. Die beibehaltene Größe für das Objekt beträgt mehrere hundert Bytes (der exakte Wert variiert).  
  
    - Dieses Objekt ist ein übrig gebliebenes Objekt von Momentaufnahme Nr. 2 und stellt einen potenziellen Speicherverlust dar.  
  
      An diesem Punkt sind Kenntnisse der app nützlich zur Verfügung: Auswählen der **Speicherverlust** Schaltfläche sollte ein DIV-Element zu entfernen und ein Element hinzugefügt, der Code scheint also nicht richtig zu funktionieren (d. h. er weist Speicher). Im nächsten Abschnitt wird beschrieben, wie die behoben werden kann.  
  
    > [!TIP]
    >  Manchmal kann das Lokalisieren eines Objekts in Bezug auf das `Global` -Objekt helfen, das Objekt zu identifizieren. Öffnen Sie hierzu das Kontextmenü für den Bezeichner, und wählen Sie dann **In Stammansicht anzeigen**aus.  
  
##  <a name="FixingMemory"></a> Korrigieren des Arbeitsspeicherproblems  
  
1. Unter Verwendung von Daten, die der Profiler erkannt hat, untersuchen Sie den Code, durch den DOM-Elemente mit der ID "item" entfernt werden. Dies tritt in der `initialize()`-Funktion auf.  
  
   ```javascript  
   function initialize() {  
  
       if (wrapper != null) {  
           elem.removeNode(true);  
       }  
   }  
   ```  
  
    Möglicherweise funktioniert`elem.removeNode(true)` nicht ordnungsgemäß. Sie untersuchen, wie der Code das DOM-Element zwischenspeichert, und finden ein Problem: Der Verweis auf das zwischengespeicherte Element wird nicht aktualisiert.  
  
2. Fügen Sie in default.js die folgende Codezeile zur Lastfunktion hinzu, unmittelbar bevor `appendChild`aufgerufen wird:  
  
   ```javascript  
   elem = newDiv;  
   ```  
  
    Dieser Code aktualisiert den Verweis auf das zwischengespeicherte Element, sodass das Element ordnungsgemäß entfernt wird, wenn Sie die Schaltfläche **Speicherverlust** auswählen. Der vollständige Code für die Lastfunktion sieht nun wie folgt aus:  
  
   ```javascript  
   function load() {  
  
       wrapper = document.querySelector(".wrapper");  
  
       var newDiv = document.createElement("div");  
  
       newDiv.style.zIndex = "-1";  
       newDiv.id = "item";  
       elem = newDiv;  
  
       wrapper.appendChild(newDiv);  
   }  
   ```  
  
3. Klicken Sie im Menü **Debuggen** auf **Leistung und Diagnose**.  
  
4. Wählen Sie unter **Verfügbare Tools**die Option **JavaScript-Memory**aus, und wählen Sie dann **Starten**.  
  
5. Befolgen Sie die gleiche Vorgehensweise wie zuvor, um drei Momentaufnahmen zu erstellen. Die erforderlichen Schritte werden hier zusammengefasst:  
  
   1. Wählen Sie in der App viermal nacheinander die Schaltfläche **Speicherverlust** aus.  
  
   2. Wechseln Sie zu Visual Studio, und wählen Sie für die Baselinemomentaufnahme **Heap-Momentaufnahme erstellen** aus.  
  
   3. Wählen Sie in der App die Schaltfläche **Speicherverlust** aus.  
  
   4. Wechseln Sie zu Visual Studio, und wählen Sie für die zweite Momentaufnahme **Heap-Momentaufnahme erstellen** aus.  
  
   5. Wählen Sie in der App die Schaltfläche **Speicherverlust** aus.  
  
   6. Wechseln Sie zu Visual Studio, und wählen Sie für die dritte Momentaufnahme **Heap-Momentaufnahme erstellen** aus.  
  
      Momentaufnahme Nr. 3 zeigt für die Heapgröße jetzt **Keine Zunahme** seit der Momentaufnahme Nr. 2 an, und der Objektzähler zeigt + 1/– 1 an, womit angegeben wird, dass ein Objekt hinzugefügt und ein Objekt entfernt wurde. Dies ist das gewünschte Verhalten.  
  
      Die folgende Abbildung zeigt Momentaufnahme Nr. 2 und Momentaufnahme Nr. 3.  
  
      ![Momentaufnahmen mit korrigiertem Arbeitsspeicherverlust](../profiling/media/js-mem-app-fixed-snapshot3.png "JS_Mem_App_Fixed_Snapshot3")  
  
## <a name="see-also"></a>Siehe auch  
 [JavaScript-Memory](../profiling/javascript-memory.md)
