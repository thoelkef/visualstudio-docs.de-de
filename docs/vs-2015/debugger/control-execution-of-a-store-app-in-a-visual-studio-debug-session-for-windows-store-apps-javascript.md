---
title: Steuern der Ausführung einer Store-app in einer Visual Studio-Debugsitzung für Windows Store-apps (JavaScript) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b5fbd27226db800a99423191126e91df1810411
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810493"
---
# <a name="control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript"></a>Steuern der Ausführung einer Store-App in einer Visual Studio-Debugsitzung für Windows Store-Apps (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Schnellstart wird veranschaulicht, wie Sie im Visual Studio-Debugger navigieren und den Programmstatus in einer Sitzung anzeigen.  
  
 Dieser Schnellstart richtet sich an Entwickler, die mit dem Debuggen in Visual Studio nicht vertraut sind, sowie an Entwickler, die mehr zum Navigieren in einer Debugsitzung in Visual Studio erfahren möchten. Das Debuggen selbst wird in diesem Schnellstart nicht erläutert. Die Funktionen im Beispielcode sollen nur die in diesem Thema beschriebenen Debugverfahren veranschaulichen. Best Practices zum Entwerfen von Apps oder Funktionen werden dabei nicht berücksichtigt. Tatsächlich werden Sie rasch feststellen, dass die Funktionen und die App selbst nicht besonders viele Aufgaben erfüllen.  
  
 Die Abschnitte dieses Schnellstarts wurden so unabhängig voneinander wie möglich konzipiert, sodass Sie einzelne Abschnitte überspringen können, die Ihnen bereits vertraute Informationen enthalten. Außerdem ist es nicht nötig, eine Beispiel-App zu erstellen. Wir empfehlen es allerdings und haben den Vorgang so einfach wie nur möglich gestaltet.  
  
 **Debugger-Tastenkombinationen.** Die Navigation im Visual Studio-Debugger wurde sowohl für die Maus als auch für die Tastatur optimiert. Für viele Schritte in diesem Thema werden die Zugriffstasten oder Tastenkombinationen in Klammern angeführt. So weist beispielsweise (Tastatur: F5) darauf hin, dass mit der F5-TASTE die Ausführung des Debuggers gestartet oder fortgesetzt wird.  
  
> [!NOTE]
>  **Das Modulmuster.**  
>   
>  Windows Store-Apps verwenden häufig das JavaScript- *Modulmuster* , um Daten und Funktionen auf einer Seite zu kapseln. Das Modulmuster verwendet einen einzelnen selbstausführenden und anonymen Abschluss, um die Funktionen der Seite vom globalen Namespace zu trennen. Im Rahmen dieses Themas bezeichnen wir diese Funktion als *Modul*.  
  
## <a name="in-this-topic"></a>In diesem Thema  
 Sie lernen Folgendes:  
  
 [Erstellen der Beispiel-App](#BKMK_Create_the_sample_app)  
  
 [Festlegen eines Haltepunkts und Ausführen bis zu diesem Haltepunkt, Durchlaufen einer Funktion in Einzelschritten und Untersuchen von Programmdaten](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)  
  
 [Einzel- und Prozedurschritte für Funktionen](#BKMK_Step_into__over__and_out_of_functions)  
  
 [Festlegen eines bedingten Haltepunkts, Ausführen bis zum Cursor und Visualisieren einer Variablen](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)  
  
 [Anzeigen von Variablendaten im Fenster "Lokal"](#BKMK_View_variable_data_in_the_Locals_window)  
  
- [Anzeigen der Variablendaten und der Prototypenkette eines Objekts](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)  
  
- [Untersuchen von Bereichskettendaten](#BKMK_Examine_scope_chain_data)  
  
  [Navigieren zum Code über das Fenster "Aufrufliste"](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)  
  
##  <a name="BKMK_Create_the_sample_app"></a> Erstellen der Beispiel-App  
 Beim Debuggen geht es um den Code. Daher wird für die Beispiel-App das Framework der Windows Store-App nur zum Erstellen einer Quelldatei verwendet, mit der Sie erkennen können, wie das Navigieren in einer Debugsitzung funktioniert und wie Sie den Programmzustand prüfen können. Der gesamte aufgerufene Code wird von der `module` -Funktion der Datei "default.js" aufgerufen. Es werden keine Steuerelemente hinzugefügt und keine Ereignisse behandelt.  
  
1. **Erstellen Sie eine leere Windows Store-App mit JavaScript.** Öffnen Sie Visual Studio. Wählen Sie auf der Homepage den Link **Neues Projekt** . Wählen Sie im Dialogfeld **Neues Projekt** in der Liste **Installiert** die Option **JavaScript** und dann **Windows Store**aus. Wählen Sie dann in der Liste der Projektvorlagen **Leere Anwendung**aus. Visual Studio erstellt eine neue Projektmappe und ein neues Projekt und zeigt die Datei "default.htm" im Code-Editor an.  
  
    Beachten Sie die Skriptdateien, die in die Seite geladen werden.  
  
   -   Die Dateien `base.js` und `ui.js` erstellen die **Windows-Bibliothek für JavaScript**. Bei der Windows-Bibliothek für JavaScript handelt es sich um einen Satz von JavaScript- und CSS-Dateien, die das Erstellen von Windows Store-Apps mit JavaScript vereinfachen. Sie verwenden sie zusammen mit HTML, CSS und Windows-Runtime zum Erstellen Ihrer App.  
  
   -   Ihr Code beginnt in der Datei `default.js`  .  
  
2. **Öffnen Sie die „default.js“-Quelldatei.** Öffnen Sie im Projektmappen-Explorer den Knoten **js** , und wählen Sie `default.js`.  
  
3. **Ersetzen Sie den Seiteninhalt durch den Beispielcode.** Löschen Sie den gesamten Inhalt aus der Datei `default.js` . Folgen Sie diesem Link: [Debugger navigation sample code (JavaScript)](../debugger/debugger-navigation-sample-code-javascript.md), und kopieren Sie anschließend den im Abschnitt JavaScript aufgelisteten Code in die Zwischenablage. (Wählen Sie **wieder** im Browser oder die Hilfe-Viewer, um zu dieser schnellstartseite zurückzukehren.) Fügen Sie den Code im Visual Studio-Editor in die jetzt leere Datei `default.js` ein. Wählen Sie **STRG+S** , um die Datei zu speichern.  
  
   Sie können nun den Beispielen in diesem Thema folgen.  
  
##  <a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Festlegen eines Haltepunkts und Ausführen bis zu diesem Haltepunkt, Durchlaufen einer Funktion in Einzelschritten und Untersuchen von Programmdaten  
 Die gängigste Methode zum Starten einer Debugsitzung besteht darin, im Menü **Debuggen** die Option **Debuggen starten** auszuwählen (Tastatur: F5). Die App wird gestartet und so lange ausgeführt, bis ein Haltepunkt erreicht wird, bis Sie sie manuell anhalten, bis eine Ausnahme auftritt, oder bis die App beendet ist.  
  
 Wenn die Ausführung im Debugger angehalten wird, können Sie den Wert einer aktiven Variablen in einem Datentipp anzeigen, indem Sie die Maus über die Variable bewegen.  
  
 Nachdem Sie die Ausführung der App angehalten haben (was auch als Debuggerunterbrechung bezeichnet wird), steuern Sie die Ausführung des übrigen Programmcodes. Sie können sie zeilenweise fortsetzen und dabei von einem Funktionsaufruf zur Funktion selbst wechseln, oder Sie können eine aufgerufene Funktion in einem einzigen Schritt ausführen. Diese Prozeduren werden als Durchlaufen der App in Einzelschritten bezeichnet. Sie können zudem die Standardausführung der App fortsetzen und bis zum nächsten festgelegten Haltepunkt oder der Codezeile ausführen, in der sich der Cursor befindet. Sie können die Debugsitzung jederzeit beenden. Der Debugger wurde entworfen, um die erforderlichen Aufräumarbeiten durchzuführen und die Ausführung zu beenden.  
  
###  <a name="BKMK_Example_1"></a> Beispiel 1  
 In diesem Beispiel legen Sie einen Haltepunkt im Hauptteil der `module` -Funktion in `default.js` fest, wenn die erste unserer Benutzeranweisungen aufgerufen wird. Anschließend durchlaufen Sie die Funktion in Einzelschritten, zeigen Variablenwerte in den Debuggerdatentipps an und beenden anschließend das Debuggen.  
  
1. **Festlegen eines Haltepunkts.** Legen Sie einen Haltepunkt bei der Anweisung `callTrack = "module function";` fest, die direkt nach dem Aufruf von `app.start()`. Wählen Sie die Zeile im schattierten Bundsteg des Quellcode-Editors aus (Tastatur: Positionieren Sie den Cursor in der Zeile, und drücken Sie **F9** ).  
  
    ![Legen Sie einen Haltepunkt bei example1](../debugger/media/dbg-jsnav-example1-breakpoint.png "DBG_JSNAV_example1_breakpoint")  
  
    Das Haltepunktsymbol wird im Bundsteg angezeigt.  
  
2. **Ausführen bis zum Haltepunkt.** Starten Sie die Debugsitzung, indem Sie im Menü **Debuggen** on the **Debuggen starten** auszuwählen (Tastatur: F5).  
  
    Die App wird ausgeführt und hält die Ausführung direkt vor der Anweisung an, in der der Haltepunkt gesetzt wurde. Das Symbol der aktuellen Zeile im Bundsteg weist auf die aktuelle Position hin, und die aktuelle Anweisung ist hervorgehoben.  
  
    ![Bis Haltepunkt ausführen](../debugger/media/dbg-jsnav-example1-run-to-breakpoint.png "DBG_JSNAV_example1_run_to_breakpoint")  
  
    Sie können die Ausführung der App nun steuern. Zudem können Sie den Programmzustand überprüfen, während Sie die Programmanweisungen durchlaufen.  
  
3. **Durchlaufen der Funktion in Einzelschritten.** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Einzelschritt** aus (Tastatur: **F11**).  
  
    ![Einzelschritt in eine einzige Zeile Code](../debugger/media/dbg-jsnav-example1-step-into.png "DBG_JSNAV_example1_step_into")  
  
    Beachten Sie, dass der Debugger zur nächsten Zeile wechselt, einem Aufruf der Funktion `example1` . Wählen Sie erneut **Einzelschritt** . Der Debugger wechselt zur ersten Codezeile der Funktion `example1` . Die hervorgehobene Zeile wurde nicht ausgeführt, aber die Funktion wurde in die Aufrufliste geladen, und der Speicher für lokale Variablen wurde zugewiesen.  
  
4. Wenn Sie einen Einzelschritt in eine Codezeile durchführen, führt der Debugger eine der folgenden Aktionen aus:  
  
   - Wenn die folgende Anweisung kein Aufruf einer Funktion Ihrer Projektmappe ist, führt der Debugger die Anweisung aus, wechselt zur folgenden Anweisung und hält dann die Ausführung an.  
  
   - Wenn es sich bei der Anweisung um den Aufruf einer Funktion in Ihrer Projektmappe handelt, wechselt der Debugger zur ersten Zeile der aufgerufenen Funktion und hält dann die Ausführung an.  
  
     Fahren Sie mit den Einzelschritten der Anweisungen von `example1` fort, bis Sie den Ausstiegspunkt erreicht haben. Der Debugger hebt die schließende geschweifte Klammer der Funktion hervor.  
  
5. **Anzeigen der Variablenwerte in den Datentipps.** Fahren Sie mit den Einzelschritten der Anweisungen von `example1` fort, bis Sie den Ausstiegspunkt erreicht haben. Der Debugger hebt die schließende geschweifte Klammer der Funktion hervor. Wenn Sie die Maus auf einen Variablennamen bewegen, werden der Name und der Wert der Variablen in einem Datentipp angezeigt.  
  
    ![Anzeigen der Variablenwerte im Datentipp](../debugger/media/dbg-jsnav-data-tip.png "DBG_JSNAV_data_tip")  
  
6. **Hinzufügen einer Überwachung für die "callTrack"-Variable.** Die Dateien `callTrack` -Variable wird in diesem Schnellstart verwendet, um die in den Beispielen aufgerufenen Funktionen anzuzeigen. Um die Anzeige des Variablenwerts zu vereinfachen, fügen Sie sie einem Überwachungsfenster hinzu. Wählen Sie den Variablennamen im Editor aus, und wählen Sie dann im Kontextmenü **Überwachung hinzufügen** .  
  
    ![Sehen Sie sich eine Variable](../debugger/media/dbg-jsnav-watch-window.png "DBG_JSNAV_watch_window")  
  
    In einem Überwachungsfenster können mehrere Variablen überwacht werden. Genau wie die Werte in Datentippfenstern werden die Werte der überwachten Variablen aktualisiert, sobald die Ausführung angehalten wird. Die überwachten Variablen werden über Debugsitzungen hinweg gespeichert.  
  
7. **Beenden des Debuggens.** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Debuggen beenden** aus (Tastatur: **UMSCHALT+F5**). Damit wird die Debugsitzung beendet.  
  
##  <a name="BKMK_Step_into__over__and_out_of_functions"></a> Einzel- und Prozedurschritte für Funktionen  
 Im Gegensatz zu einem Einzelschritt in eine Funktion, die von einer übergeordneten Funktion aufgerufen wird, wird bei einem Prozedurschritt die untergeordnete Funktion ausgeführt und die Ausführung anschließend in der aufrufenden Funktion angehalten, wenn die übergeordnete Funktion fortgesetzt wird. Sie können für eine Funktion einen Prozedurschritt ausführen, wenn Sie mit der Funktionsweise der Funktion vertraut und sicher sind, dass deren Ausführung das zu untersuchende Problem nicht beeinflusst.  
  
 Bei einem Prozedurschritt für eine Codezeile, die keinen Funktionsaufruf enthält, wird die Zeile wie bei einem Einzelschritt ausgeführt.  
  
 Beim Ausführen von einer untergeordneten Funktion aus wird die Ausführung der Funktion fortgesetzt und dann angehalten, wenn die Funktion zu ihrer aufrufenden Funktion zurückkehrt. Sie können einen Prozedurschritt aus einer langen Funktion durchführen, wenn Sie erkannt haben, dass der Rest der Funktion nicht relevant ist.  
  
 Bei Prozedurschritten aus einer Funktion wird diese ausgeführt.  
  
 ![Schritt in, und Prozedurschritte für Methoden](../debugger/media/dbg-basics-stepintooverout.png "DBG_Basics_StepIntoOverOut")  
  
###  <a name="BKMK_Example_2"></a> Beispiel 2  
 In diesem Beispiel führen Sie Einzel- und Prozedurschritte für Funktionen aus.  
  
1.  **Aufrufen der Funktion "example2" in der Modulfunktion.** Bearbeiten Sie die `module` -Funktion, und ersetzen Sie die Zeile nach `var callTrack = "module function"` durch `example2();`.  
  
     ![Rufen Sie die Funktion "example2"](../debugger/media/dbg-jsnav-example2.png "DBG_JSNAV_example2")  
  
2.  **Ausführen bis zum Haltepunkt.** Starten Sie die Debugsitzung, indem Sie im Menü **Debuggen** on the **Debuggen starten** auszuwählen (Tastatur: F5). Der Debugger unterbricht die Ausführung am Haltepunkt.  
  
3.  **Prozedurschritt für die Codezeile.** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Prozedurschritt** aus (Tastatur: F10). Der Debugger führt die `var callTrack = "module function"` -Anweisung auf die gleiche Weise wie den Einzelschritt in die Anweisung aus.  
  
4.  **Einzelschritt in "example2" und "example2_A".** Drücken Sie **F11** , um einen Einzelschritt für die `example2` . Durchlaufen Sie die `example2` -Anweisungen weiterhin in Einzelschritten, bis Sie die Zeile `var x = example2_a();`erreichen. Führen Sie erneut für diese Zeile einen Einzelschritt durch, um zum Einstiegspunkt von `example2_a`zu gelangen. Durchlaufen Sie die einzelnen Anweisungen von `example2_a` in Einzelschritten, bis Sie zu `example2`zurückkehren.  
  
     ![Prozedurschritt für eine Funktion](../debugger/media/dbg-jsnav-example2-a.png "DBG_JSNAV_example2_a")  
  
5.  **Prozedurschritt für eine Funktion.** Beachten Sie, dass die nächste Zeile in `example2`( `var y = example2_a();` ) im Wesentlichen der vorherigen Zeile entspricht. Sie können problemlos einen Prozedurschritt für diese Zeile durchführen. Drücken Sie die Taste **F10** , um von der Fortsetzung von `example2` zu diesem zweiten Aufruf von `example2_a`zu wechseln. Beachten Sie, dass die Zeichenfolge `callTrack` auf eine zweimalige Ausführung der `example2_a` -Funktion hinweist.  
  
6.  **Prozedurschritt aus einer Funktion.** Drücken Sie **F11** , um einen Einzelschritt für die `example2_b` . Beachten Sie, dass `example2_b` sich kaum von `example2_a`unterscheidet. Um einen Prozedurschritt aus der Funktion durchzuführen, wählen Sie im Menü **Debuggen** die Option **Prozedurschritt** aus (Tastatur: **UMSCHALT+F11**). Beachten Sie, dass die Variable `callTrack` angibt, dass `example2_b` ausgeführt wurde und dass der Debugger zu dem Punkt zurückgekehrt ist, an dem `example2` fortgesetzt wird.  
  
7.  **Beenden des Debuggens.** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Debuggen beenden** aus (Tastatur: **UMSCHALT+F5**). Damit wird die Debugsitzung beendet.  
  
##  <a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Festlegen eines bedingten Haltepunkts, Ausführen bis zum Cursor und Visualisieren einer Variablen  
 Ein bedingter Haltepunkt legt eine Bedingung fest, unter der der Debugger die Ausführung unterbricht. Die Bedingung kann mit beliebigen Codeausdrücken angegeben werden, die als "true" oder "false" ausgewertet werden können. So können Sie beispielsweise einen bedingten Haltepunkt nur dann zum Prüfen des Programmzustands einer häufig aufgerufenen Funktion verwenden, wenn eine Variable einen bestimmten Wert erreicht.  
  
 Das Ausführen bis zum Cursor entspricht dem Festlegen eines einmaligen Haltepunkts. Wenn die Ausführung angehalten wird, können Sie eine Zeile in der Quelle auswählen und die Ausführung fortsetzen, bis die ausgewählte Zeile erreicht ist. So können Sie beispielsweise eine Schleife in einer Funktion in Einzelschritten durchlaufen und feststellen, dass der Code in der Schleife ordnungsgemäß ausgeführt wird. Anstatt alle Iterationen der Schleife zu durchlaufen, können Sie bis zum Cursor ausführen, der nach dem Ausführen der Schleife positioniert wird.  
  
 Mitunter ist es schwierig, einen Variablenwert in der Zeile eines Datentipp- oder sonstigen Datenfensters anzuzeigen. Der Debugger kann Zeichenfolgen, HTML und XML in einer Text-Schnellansicht anzeigen, die eine formatierte Ansicht des Werts in einem bildlauffähigen Fenster darstellt.  
  
###  <a name="BKMK_Example_3"></a> Beispiel 3  
 In diesem Beispiel legen Sie einen bedingten Haltepunkt fest, um an einer bestimmten Iteration einer Schleife zu unterbrechen und anschließend bis zum nach der Schleife positionierten Cursor auszuführen. Zudem wird der Wert der Variablen in einer Text-Schnellansicht angezeigt.  
  
1.  **Aufrufen der Funktion "example3" in der Modulfunktion.** Bearbeiten Sie die `module` -Funktion, und ersetzen Sie die Zeile nach `var callTrack = "module function";` durch die Zeile `example3();`.  
  
     ![Example3 Aufrufen](../debugger/media/dbg-jsnav-example3.png "DBG_JSNAV_example3")  
  
2.  **Ausführen bis zum Haltepunkt.** Starten Sie die Debugsitzung, indem Sie im Menü **Debuggen** on the **Debuggen starten** aus (Tastatur: **F5**). Der Debugger hält die Ausführung am Haltepunkt in der `module` -Funktion an.  
  
3.  **Einzelschritt in die Funktion "example3"** Wählen Sie **Einzelschritt** on the **Debuggen starten** aus (Tastatur: **F11**), um zum Einstiegspunkt der Funktion `example3` . Durchlaufen Sie die Funktion in Einzelschritten, bis Sie eine oder zwei Schleifen des `for` -Blocks durchlaufen haben. Beachten Sie, dass es sehr lange dauern würde, alle 1000 Iterationen zu durchlaufen.  
  
4.  **Festlegen eines bedingten Haltepunkts.** Klicken Sie im linken Bundsteg des Codefensters mit der rechten Maustaste auf die Zeile `s += i.toString() + "\n";` , und wählen Sie dann im Kontextmenü die Option **Bedingung** aus.  
  
     Aktivieren Sie das Kontrollkästchen **Bedingung** , und geben Sie dann im Textfeld `i == 500;` ein. Wählen Sie die Option **Ist "True"** und anschließend **OK**aus. Mithilfe des Haltepunkts können Sie den Wert an der 500. Iteration der `for` -Schleife überprüfen. Sie erkennen das Symbol eines bedingten Haltepunkts am weißen Kreuz.  
  
     ![Symbol "bedingter Haltepunkt"](../debugger/media/dbg-jsnav-breakpoint-condition-icon.png "DBG_JSNAV_Breakpoint_Condition_icon")  
  
5.  **Ausführen bis zum Haltepunkt.** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Weiter** aus (Tastatur: **F5**). Halten Sie den Mauszeiger auf `i` , um sicherzustellen, dass der aktuelle Wert von `i` 500 lautet. Beachten Sie, dass die Variable `s` als einzelne Zeile dargestellt wird, die weit über das Datentippfenster hinausgeht.  
  
6.  **Visualisieren einer Zeichenfolgenvariablen.** Klicken Sie in der Spalte Wert von `s`.  
  
     Das Text-Schnellansichtsfenster wird angezeigt, in dem der Wert der Zeichenfolge als mehrzeilige Zeichenfolge dargestellt wird.  
  
     ![Text-Schnellansicht Debuggen](../debugger/media/dbg-jsnav-text-visualizer.png "DBG_JSNAV_Text_Visualizer")  
  
7.  **Ausführen bis zum Cursor.** Klicken Sie mit der rechten Maustaste auf die Zeile `callTrack += "->example3";` , und wählen Sie dann im Kontextmenü die Option **Ausführen bis Cursor** (Tastatur: **STRG + F10**). Der Debugger schließt die Schleifeniterationen ab und hält anschließend die Ausführung an der Zeile an.  
  
8.  **Beenden des Debuggens.** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Debuggen beenden** aus (Tastatur: **UMSCHALT+F5**). Damit wird die Debugsitzung beendet.  
  
###  <a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Verwenden von "Ausführen bis Cursor" zum Zurückkehren zum Code und zum Löschen eines Haltepunkts.  
 Die Ausführung bis zum Cursor kann sehr nützlich sein, wenn Sie Bibliothekscode von Microsoft oder einem Drittanbieter in Einzelschritten durchlaufen. Das Durchlaufen von Bibliothekscode kann sehr informativ sein, jedoch oft auch sehr lange dauern. In der Regel sind Sie wesentlich mehr an Ihrem eigenen Code interessiert. Diese Übung zeigt Ihnen, wie es geht.  
  
1.  **Legen Sie einen Haltepunkt beim app.start-Aufruf fest.** In the `module` -Funktion einen Haltepunkt an der Zeile `app.start()`  
  
2.  **Ausführen bis zum Haltepunkt und Durchlaufen der Bibliotheksfunktion in Einzelschritten.**  
  
     Wenn Sie `app.start()`in Einzelschritten durchlaufen, wird der Code in `base.js`im Editor angezeigt. Führen Sie einige weitere Einzelschritte durch.  
  
3.  **Prozedurschritte für und aus Funktionen.** Wenn Sie Prozedurschritte für (**F10**) und aus (**SHIFT+F11**) Code in `base.js`durchführen, gelangen Sie möglicherweise zu dem Schluss, dass Sie die Komplexität und die Länge der Startfunktion eigentlich nicht untersuchen möchten.  
  
4.  **Festlegen des Cursors auf Ihren Code und Ausführen bis zum Cursor.** Wechseln Sie im Code-Editor zurück zur Datei `default.js` . Wählen Sie die erste Zeile des Codes nach `app.start()` . (Die Ausführung bis zu einem Kommentar oder einer leeren Zeile ist nicht möglich.) Wählen Sie im Kontextmenü **Ausführen bis Cursor** . Der Debugger setzt die Ausführung der app.start-Funktion fort und hält sie beim Haltepunkt an.  
  
##  <a name="BKMK_View_variable_data_in_the_Locals_window"></a> Anzeigen von Variablendaten im Fenster "Lokal"  
 Das Fenster "Lokal" ist eine Strukturansicht der Parameter und Variablen in der Bereichskette der aktuell ausgeführten Funktion.  
  
###  <a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Anzeigen der Variablendaten und der Prototypenkette eines Objekts  
  
1.  **Hinzufügen eines Arrayobjekts zur Modulfunktion** Bearbeiten Sie die `module` -Funktion, und ersetzen Sie die Zeile nach `var callTrack = "module function"` durch `var myArray = new Array(1, 2, 3);`  
  
     ![MyArray-Definition](../debugger/media/dbg-jsnav-myarray.png "DBG_JSNAV_myArray")  
  
2.  **Ausführen bis zum Haltepunkt.** Starten Sie die Debugsitzung, indem Sie im Menü **Debuggen** on the **Debuggen starten** aus (Tastatur: **F5**). Der Debugger unterbricht die Ausführung am Haltepunkt. Führen Sie einen Einzelschritt in die Zeile durch.  
  
3.  **Öffnen Sie das Fenster "Lokal".** On the **Debuggen** auf **Fenster**, und wählen Sie **Lokale**aus. (Tastatur: Alt+4).  
  
4.  **Überprüfen der lokalen Variablen in der Modulfunktion** Das Fenster "Lokal" zeigt die Variablen der aktuell ausgeführten Funktion (der `module` -Funktion) als Knoten der obersten Ebene der Struktur an. Wenn Sie eine Funktion eingeben, erstellt JavaScript alle Variablen und weist ihnen den Wert `undefined`zu. Bei den in der Funktion definierten Funktionen entspricht der Wert ihrem Text.  
  
     ![Fenster "lokal"](../debugger/media/dbg-jsnav-locals-window.png "DBG_JSNAV_Locals_window")  
  
5.  **Durchlaufen der callTrack- und myArray-Definitionen.** Suchen Sie im Fenster "Lokal" die Variablen "callTrack" und "myArray". Führen Sie für die beiden Definitionen einen Prozedurschritt (**F10**) durch, und beachten Sie, dass die Felder **Wert** und **Typ** geändert wurden. Im Fenster "Lokal" werden die Werte von Variablen hervorgehoben, die sich seit der letzten Unterbrechung geändert haben.  
  
6.  **Untersuchen des MyArray-Objekts** Erweitern Sie die `myArray` -Variable. Jedes Element des Arrays wird im Knoten **[Prototyp]** aufgeführt, der die Vererbungshierarchie des `Array` -Objekts enthält. Erweitern Sie diesen Knoten.  
  
     ![Prototypkette im Lokalfenster](../debugger/media/dbg-jsnav-locals-proto-chain.png "DBG_JSNAV_Locals_proto_chain")  
  
    -   Im Knoten **Methoden** werden alle Methoden des `Array` -Objekts aufgeführt.  
  
    -   Der Knoten **[Prototyp]** enthält den Prototyp des `Object` -Objekts, aus dem `Array` abgeleitet wird. **[Prototyp]** -Knoten können rekursiv sein. Jedes übergeordnete Objekt in einer Objekthierarchie wird im **[Prototyp]** -Knoten des untergeordneten Elements beschrieben.  
  
7.  **Beenden des Debuggens.** On the **Debuggen** die Option **Debuggen beenden** aus (Tastatur: UMSCHALT+F5). Damit wird die Debugsitzung beendet.  
  
##  <a name="BKMK_Examine_scope_chain_data"></a> Untersuchen von Bereichskettendaten  
 Die *Bereichskette* einer Funktion enthält alle Variablen, die aktiv sind und von der Funktion erreicht werden können. Globale Variablen sind Teil der Bereichskette, ebenso wie alle Objekte (einschließlich Funktionen), die in der Funktion definiert werden, die wiederum die derzeit ausgeführte Funktion definiert. Beispielsweise ist die `callTrack` -Variable, die in der `module` -Funktion von `default.js` definiert ist, von jeder Funktion erreichbar, die in der `module` -Funktion definiert ist. Jeder Bereich wird im Fenster "Lokal" separat aufgeführt.  
  
- Die Variablen der aktuell ausgeführten Funktion werden im oberen Fensterbereich aufgeführt.  
  
- Die Variablen für die einzelnen Funktionsbereiche in der Bereichskette werden unter einem Knoten **[Bereich]** für die Funktion aufgeführt. Die Bereichsfunktionen werden nach ihrer Reihenfolge in der Kette aufgelistet, von der Funktion, die die aktuelle Funktion definiert, bis hin zur äußersten Funktion in der Kette.  
  
- Der Knoten **[Global]** enthält die globalen Objekte, die unabhängig von den Funktionen definiert werden.  
  
  Bereichsketten können verwirrend sein und lassen sich am besten anhand eines Beispiels erläutern. Im folgenden Beispiel sehen Sie, wie die `module` -Funktion einen eigenen Bereich erstellt und wie Sie eine weitere Bereichsebene durch das Erstellen eines Abschlusses erstellen können.  
  
###  <a name="BKMK_Example_4"></a> Beispiel 4  
  
1.  **Aufrufen der Funktion "example4" in der Modulfunktion.** Bearbeiten Sie die `module` -Funktion, und ersetzen Sie die Zeile nach `var callTrack = "module function"` durch `example4()`:  
  
     ![Aufrufen von "example4"](../debugger/media/dbg-jsnav-example4.png "DBG_JSNAV_example4")  
  
2.  **Ausführen bis zum Haltepunkt.** Starten Sie die Debugsitzung, indem Sie im Menü **Debuggen** on the **Debuggen starten** aus (Tastatur: **F5**). Der Debugger unterbricht die Ausführung am Haltepunkt.  
  
3.  **Öffnen Sie das Fenster "Lokal".** Zeigen Sie ggf. im Menü **Debuggen starten** auf **Fenster**, und wählen Sie **Lokale**. (Tastatur: **ALT+4**). Beachten Sie, dass im Fenster alle Variablen und Funktionen der `module` -Funktion aufgelistet werden und dass auch ein Knoten **[Global]** angezeigt wird.  
  
4.  **Überprüfen der globalen Variablen.** Erweitern Sie die **[Global]** angezeigt wird. Die Objekte und Variablen unter "Global" wurden von der Windows-Bibliothek für JavaScript festgelegt. Sie können dem globalen Bereich Ihre eigenen Variablen hinzufügen.  
  
5.  **Durchlaufen von "example4" in Einzelschritten und Untersuchen der lokalen und der Bereichsvariablen** Durchlaufen Sie die **-Funktion in Einzelschritten (Tastatur:** F11 `example4` ). Da `example4` in der `module` -Funktion definiert ist, wird die `module` -Funktion zum übergeordneten Bereich. `example4` kann jede der Funktionen in der `module` -Funktion aufrufen und auf ihre Variablen zugreifen. Erweitern Sie den Knoten **[Bereich]** im Fenster "Lokal", und beachten Sie, dass er dieselben Variablen der `module` -Funktion enthält.  
  
     ![Bereiche der example4-Methode](../debugger/media/dbg-jsnav-locals-example4-scope.png "DBG_JSNAV_Locals_example4_scope")  
  
6.  **Durchlaufen von "example4_a" in Einzelschritten und Untersuchen der lokalen und der Bereichsvariablen** Durchlaufen Sie `example4` und den Aufruf von `example4_a`weiterhin in Einzelschritten. Beachten Sie, dass die lokalen Variablen jetzt von `example4_a`stammen und dass der Knoten **[Bereich]** weiterhin die Variablen der `module` -Funktion enthält. Obwohl die Variablen von `example4` aktiv sind, können sie von `example4_a` nicht erreicht werden und sind nicht mehr Bestandteil der Bereichskette.  
  
7.  **Durchlaufen von "multipyByA" in Einzelschritten und Untersuchen der lokalen und der Bereichsvariablen** Durchlaufen Sie den Rest von `example4_a` in Einzelschritten bis zur Zeile `var x = multilpyByA(b);`.  
  
     Die Funktionsvariable `multipyByA` wurde auf die `multiplyClosure` -Funktion festgelegt, bei der es sich um einen *Abschluss*handelt. `multipyClosure` definiert und gibt eine innere Funktion zurück ( `mulitplyXby`). Außerdem werden ihr Parameter und ihre Variable erfasst (geschlossen). In einem Abschluss kann die zurückgegebene innere Funktion auf die Daten der äußeren Funktion zugreifen und so eine eigene Bereichsebene erstellen.  
  
     Wenn Sie `var x = multilpyByA(b);`in Einzelschritten durchlaufen, gelangen Sie zur Zeile `return a * b;` in der inneren Funktion `mulitplyXby` .  
  
8.  Im Fenster "Lokal" wird nur der `b` -Parameter als lokale Variable in `multiplyXby`aufgeführt, es wurde jedoch eine neue **[Bereich]** -Ebene hinzugefügt. Beim Erweitern dieses Knotens sehen Sie, dass diese die Parameter, Funktionen und Variablen von `multiplyClosure`umfasst, einschließlich der `a` -Variable, die in der ersten Zeile von `multiplyXby`aufgerufen wurde. Eine schnelle Überprüfung des zweiten **[Bereich]** -Knotens zeigt die Variablen der Modulfunktion, auf die `multiplyXby` in der nächsten Zeile zugreift.  
  
     ![Bereiche eines Schließvorgangs im Lokalfenster](../debugger/media/dbg-jsnav-scope-mulitplyxby.png "DBG_JSNAV_scope_mulitplyXby")  
  
9. **Beenden des Debuggens.** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Debuggen beenden** aus (Tastatur: **UMSCHALT+F5**). Damit wird die Debugsitzung beendet.  
  
##  <a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Navigieren zum Code über das Fenster "Aufrufliste"  
 Die Aufrufliste ist eine Datenstruktur, die Informationen zu den Funktionen enthält, die im aktuellen Thread der Anwendung ausgeführt werden. Wenn ein Haltepunkt erreicht wird, zeigt das Fenster "Aufrufliste" eine Liste aller Funktionen an, die in der Liste aktiv sind. Die aktuell ausgeführte Funktion wird am Anfang der Liste im Fenster "Aufrufliste" aufgeführt. Die Funktion, die den Thread initiiert, befindet sich am Ende der Liste. Die Funktionen dazwischen zeigen den Aufrufpfad der initiierenden Funktion bis hin zur aktuellen Funktion.  
  
 Neben der Anzeige des Aufrufpfads bis hin zur derzeit ausgeführten Funktion dient das Fenster "Aufrufliste" auch zum Navigieren zu Code im Code-Editor. Diese Funktionalität kann nützlich sein, wenn Sie mit mehreren Dateien arbeiten und schnell zu einer bestimmten Funktion gelangen möchten.  
  
###  <a name="BKMK_Example_5"></a> Beispiel 5  
 In diesem Beispiel durchlaufen Sie einen Aufrufpfad in Einzelschritten, der fünf benutzerdefinierte Funktionen enthält.  
  
1.  **Aufrufen der Funktion "example5" in der Modulfunktion.** Bearbeiten Sie die `module` -Funktion, und ersetzen Sie die Zeile nach `var callTrack = "module function";` durch die Zeile `example5();`.  
  
     ![Example5 Aufrufen](../debugger/media/dbg-jsnav-example5.png "DBG_JSNAV_example5")  
  
2.  **Ausführen bis zum Haltepunkt.** Starten Sie die Debugsitzung, indem Sie im Menü **Debuggen** on the **Debuggen starten** aus (Tastatur: **F5**). Der Debugger hält die Ausführung am Haltepunkt in der Modulfunktion an.  
  
3.  **Öffnen des Fensters "Aufrufliste".** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Fenster**, und wählen Sie **Aufrufliste** (Tastatur: ALT+7). Beachten Sie, dass im Fenster "Aufrufliste" zwei Funktionen angezeigt werden:  
  
    -   **Globaler Code** ist der Einstiegspunkt der `module` -Funktion am unteren Ende der Aufrufliste.  
  
    -   **Anonyme Funktion** zeigt die Zeile in der `module` -Funktion an, bei der die Ausführung angehalten wird. Dies ist der Anfang der Aufrufliste.  
  
4.  **Durchlaufen von Funktionen in Einzelschritten zum Erreichen der Funktion "example5_d".** Wählen Sie **Einzelschritt** auf die **Debuggen** Menü (Tastatur: **F11**) um die Aufrufe im Aufrufpfad auszuführen, bis zu den Einstiegspunkt der example5_d-Funktion. Beachten Sie, dass die Zeilennummer der aufrufenden Funktion bei jedem Aufruf einer Funktion gespeichert wird und dass die aufgerufene Funktion an den Anfang der Liste platziert wird. Die Zeilennummer der aufrufenden Funktion ist der Punkt, an dem die aufrufende Funktion die Ausführung angehalten hat. Ein gelber Pfeil zeigt auf die gerade ausgeführte Funktion.  
  
     ![Fenster "Aufrufliste"](../debugger/media/dbg-jsnav-callstack-windows.png "DBG_JSNAV_CallStack_windows")  
  
5.  **Verwenden des Fensters "Aufrufliste" zum Navigieren zum Code von "example5_a" und Festlegen eines Haltepunkts.** Wählen Sie im Fenster "Aufrufliste" das Element `example5_a` aus, und wählen Sie dann im Kontextmenü die Option **Gehe zu Quellcode** aus. Der Code-Editor setzt den Cursor auf die Rückgabezeile der Funktion. Legen Sie einen Haltepunkt in dieser Zeile fest. Beachten Sie, dass die aktuelle Ausführungszeile nicht geändert wird. Nur der Editor-Cursor wurde verschoben.  
  
6.  **Durchlaufen von Funktionen in Einzelschritten und dann Ausführen bis zum Haltepunkt.** Durchlaufen Sie `example5_d`. Beachten Sie, dass die Funktion aus der Aufrufliste entfernt wird, wenn Sie von der Funktion zurückkehren. Drücken Sie **F5** , um die Ausführung des Programms fortzusetzen. Sie beenden die Ausführung am Haltepunkt, den Sie im vorherigen Schritt erstellt haben.  
  
7.  **Beenden des Debuggens.** Wählen Sie im Dialogfeld **Debuggen starten** die Option **Debuggen beenden** aus (Tastatur: **UMSCHALT+F5**). Damit wird die Debugsitzung beendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten einer Debugsitzung (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)   
 [Schnellstart: Debuggernavigation (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Auslösen anhalten, fortsetzen und hintergrundereignissen für Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Debuggen von Apps in Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)



