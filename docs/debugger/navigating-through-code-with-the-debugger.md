---
title: Navigieren Sie im Code mit dem Debugger in Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ae96b360620a58fa323d080e6262c7f2966fa160
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="navigate-code-with-the-visual-studio-debugger"></a>Navigieren Sie im Code mit Visual Studio-Debugger
Mit den Befehlen und Tastenkombinationen zum Navigieren im Code im Debugger vertraut machen, und treffen, die zum Suchen und beheben Probleme in Ihrer app leichter und schneller. Während Sie den Code im Debugger navigieren, können Sie überprüfen Sie den Status der app oder erfahren Sie mehr über seine Ausführungsfluss.  
  
## <a name="start-debugging"></a>Debugging starten  
 Häufig, Sie beginnen, ein debugging Sitzung mit **F5** (**Debuggen** > **Debuggen**). Mit diesem Befehl wird Ihre app mit dem angefügten Debugger gestartet.  
  
 Der grüne Pfeil wird auch der Debugger gestartet (identisch mit **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg_basics_start_debugging.png "DBG_Basics_Start_Debugging")  
  
 Einige andere, dass Sie die app, mit dem angefügten Debugger starten können Konfigurationsmethoden **F11** ([Einzelschritt in Code](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([Prozedurschritt Code](#BKMK_Step_over_Step_out)), oder durch mit **Ausführen bis Cursor**.  Finden Sie in den weiteren Abschnitten in diesem Thema Informationen zu den Schritten dieser Optionen ausführen.  
  
 Beim Debuggen zeigt die gelbe Zeile Sie den Code, der als Nächstes ausgeführt wird.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg_basics_break_mode.png "DBG_Basics_Break_Mode")  
  
 Während des Debuggens können Sie wechseln zwischen Befehlen wie **F5**, **F11** und andere Funktionen in diesem Thema (z. B. Haltepunkte) beschrieben werden, um schnell auf den Code erhalten Sie betrachten möchten.  
  
 Die meisten Debuggerfunktionen, z. B. die Anzeige von Variablenwerten im Fenster "lokal" oder das Auswerten von Ausdrücken im Überwachungsfenster, stehen nur verwendet werden, während der Debugger angehalten wird (so genannte *Unterbrechungsmodus*). Wenn der Debugger angehalten wird, der app-Zustand wird angehalten, während der Funktionen, Variablen und Objekte im Speicher verbleiben. Klicken Sie im Unterbrechungsmodus befinden, können Sie die Elemente Positionen und Zustände, um nach Verstößen oder Fehlern zu suchen untersuchen. Für manche Projekttypen können Sie auch anpassen, um die app im Unterbrechungsmodus vornehmen. Um ein Video mit diesen Funktionen zu beobachten, finden Sie unter [erste Schritte mit dem Debugger](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Einzelschritt in Code zeilenweise  
 Um während des Debuggens in jeder Zeile des Codes (jede Anweisung) zu beenden, verwenden die **F11** Tastenkombination (oder **Debuggen** > **Einzelschritt** im Menü).  
  
> [!TIP]
>  Wenn Sie mit jeder Codezeile ausführen, können Sie Variablen, deren Werte angezeigt werden soll, oder verwenden Sie zeigen die ["lokal"](../debugger/autos-and-locals-windows.md) und [Überwachen](../debugger/autos-and-locals-windows.md) Windows, um deren Werte ändern zu beobachten.  
  
 Hier sind einige Details über das Verhalten des **Einzelschritt**:  
  
-   Bei einem geschachtelten Funktionsaufruf führt **Einzelschritt** die am tiefsten geschachtelte Funktion in Einzelschritten aus. Wenn Sie **Einzelschritt** für einen Aufruf wie `Func1(Func2())`verwenden, führt der Debugger die Funktion `Func2`in Einzelschritten aus.  
  
-   Der Debugger durchläuft tatsächlich durch Codeanweisungen anstatt durch physische Zeilen. Beispielsweise kann eine `if`-Klausel in eine Zeile geschrieben werden:  
  
    ```csharp  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```VB  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Wenn Sie einen Einzelschritt in diese Zeile ausführen, behandelt der Debugger die Bedingung als einen Schritt und das Ergebnis als anderen Schritt (in diesem Beispiel lautet die Bedingung "true").  
  
 Um die Aufrufliste während der schrittweisen Funktionen visuell zu verfolgen, finden Sie unter [Zuordnen von Methoden in der Aufrufliste während des Debuggens](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> Durchlaufen von Code, überspringen die Funktionen  
 Wenn Code im Debugger ausgeführt wird, oft erkennen Sie, dass Sie benötigen, um festzustellen, was geschieht, in einer bestimmten Funktion (nicht wichtig er oder Sie wissen, dass sie funktioniert, wie die getestete Bibliothekscode). Diese Befehle verwenden, um Code zu überspringen (die Funktionen weiterhin ausgeführt, natürlich, aber der Debugger überspringt sie).  
  
|Tastenkombination|Menübefehl|Beschreibung|  
|----------------------|------------------|-----------------|  
|**F10**|**Prozedurschritt**|Wenn die aktuelle Zeile einen Funktionsaufruf enthält **Prozedurschritt** führt den Code, und klicken Sie dann in der ersten Zeile des Codes angehalten, wenn die aufgerufene Funktion zurückkehrt.|  
|**UMSCHALT + F11**|**Ausführen bis Rücksprung**|**Ausführen bis Rücksprung** setzt die Ausführung von Code und hält bei Rückgabe von der aktuellen Funktion (der Debugger überspringt über die aktuelle Funktion).|  
  
> [!TIP]
>  Sie müssen den Einstiegspunkt in Ihre app zu suchen, beginnen Sie mit **F10** oder **F11**. Diese Befehle sind oft hilfreich, wenn Sie Ihrer app-Status überprüfen oder Weitere Informationen über seine Ausführungsfluss erhalten möchten.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Führen Sie an einer bestimmten Position oder Funktion  
 Häufig die bevorzugte Methode für das Debuggen von Code diese Methoden sind nützlich, wenn Sie genau Codes kennen Sie überprüfen möchten, oder mindestens Sie wissen, wo Sie mit dem Debuggen beginnen möchten.  
  
-   **Festlegen von Haltepunkten im Code**  
  
     Um einen einfachen Haltepunkt im Code festzulegen, öffnen Sie die Quellcodedatei im Visual Studio-Editor. Setzen Sie den Cursor in die Codezeile, wo möchten Sie unterbrechen die Ausführung, und klicken Sie dann mit der rechten Maustaste im Codefenster "finden im Kontextmenü den Befehl aus, und wählen **Haltepunkt > Haltepunkt einfügen** (oder drücken Sie **F9**). Der Debugger unterbricht die Ausführung rechts, bevor die Zeile ausgeführt wird.  
  
     ![Festlegen eines Haltepunkts](../debugger/media/dbg_basics_setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Haltepunkte in Visual Studio bieten einen umfangreichen Satz von zusätzlichen Funktionen, wie z. B. bedingte Haltepunkte und Ablaufverfolgungspunkte. Finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).  
  
-   **Ausführen bis zur Cursorplatzierung**  
  
     Um den Code bis zur Cursorposition auszuführen, platzieren Sie den Cursor in einem Quellcodefenster auf eine ausführbare Codezeile. Wählen Sie in der Editor-Kontextmenü (Rechtsklick im Editor), **Ausführen bis Cursor**. Dies entspricht dem Festlegen eines Haltepunkts temporäre.

-   **Klicken Sie auf Ausführen** 

    Wählen Sie zum Ausführen auf einen Punkt im Code im Debugger Anhalten der **hier ausgeführt** grünen Pfeil (angezeigt, das Symbol "Wenn Sie mit dem Mauszeiger auf eine Codezeile). Hierdurch entfällt die Notwendigkeit temporäre Haltepunkte festgelegt.

    ![Der Debugger ausgeführt wird, klicken Sie auf](../debugger/media/dbg-run-to-click.png "DbgRunToClick") 

    > [!NOTE]
    > **Klicken Sie auf Ausführen** ist neu in [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].
  
-   **Manuelles Unterbrechen im Code**  
  
     Um die Ausführung einer Anwendung in der nächsten verfügbaren Codezeile zu unterbrechen, wählen Sie **Debuggen**, **Alle unterbrechen** (Tastatur: **Ctrl+Alt+Break**). 
  
     Wenn Sie die Ausführung von Code ohne zugehörige Quell- oder Symboldateien (PDB-Dateien) unterbrechen, wird im Debugger die Seite **Die Quelldatei wurde nicht gefunden** oder **Symbol nicht gefunden** geöffnet, auf der Sie die entsprechenden Dateien suchen können. Finden Sie unter [angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Wenn Sie nicht auf die zugehörigen Hilfsdateien zugreifen können, können Sie dennoch die Assemblyanweisungen im Disassemblyfenster debuggen.  
  
-   **Ausführen bis zu einer Funktion in der Aufrufliste**  
  
     In der **Aufrufliste** Fenster (während des Debuggens verfügbar), wählen Sie die Funktion, mit der rechten Maustaste und wählen Sie **Ausführen bis Cursor**. Um die Aufrufliste visuell zu verfolgen, finden Sie unter [Zuordnen von Methoden in der Aufrufliste während des Debuggens](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Ausführen bis zu einer Funktion anhand des Namens**  
  
     Sie können feststellen, dass den Debugger an die Anwendung auszuführen, bis eine bestimmte Funktion erreicht. Sie können die Funktion anhand ihres Namens angeben oder in der Aufrufliste auswählen.  
  
     Um eine Funktion anhand des Namens anzugeben, wählen Sie **Debuggen**, **Neuer Haltepunkt**, **Halten bei Funktion**aus, und geben Sie dann den Namen der Funktion und andere Identifikationsinformationen ein.  
  
     ![Dialogfeld "neue Haltepunkt"](../debugger/media/dbg_execution_newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Wenn die Funktion überladen ist oder sich in mehreren Namespaces befindet, können Sie die gewünschten Funktionen im Dialogfeld **Haltepunkte wählen** auswählen.  
  
     ![Wählen Sie im Dialogfeld Breakpoints](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Ziehen Sie den Mauszeiger, um den Ausführungsfluss zu ändern  
 Während der Debugger angehalten wird, können Sie den Anweisungszeiger zum Festlegen der nächsten Anweisung der auszuführende Code verschieben. Die Position der nächsten auszuführenden Anweisung wird durch eine gelbe Pfeilspitze am Rand eines Quellcodefensters oder Disassemblierungsfensters markiert. Durch das Verschieben dieser Pfeilspitze können Sie einen Teil des Codes überspringen oder zu einer bereits ausgeführten Zeile zurückkehren. Dies ist zum Beispiel sinnvoll, um einen Codeabschnitt zu überspringen, von dem bereits bekannt ist, dass er einen Fehler enthält.  
  
 ![Bewegen des Mauszeigers](../debugger/media/dbg_basics_example3.gif "DBG_Basics_Example3")
  
 Zum Festlegen der nächsten auszuführenden Anweisung verwenden Sie eines der folgenden Verfahren:  
  
-   Ziehen Sie die gelbe Pfeilspitze in einem Quellcodefenster in derselben Quelldatei an die Position, an der Sie die nächste Anweisung festlegen möchten.  
  
-   Setzen Sie den Cursor in einem Quellcodefenster in der Zeile, die Sie als Nächstes ausführen, mit der rechten Maustaste, und wählen möchten **nächste Anweisung festlegen**.  
  
-   Setzen Sie den Cursor im dissamblyfenster auf die Assemblyanweisung, die Sie verwenden möchten, als Nächstes ausführen, mit der rechten Maustaste ein, und wählen Sie **nächste Anweisung festlegen**.  
  
> [!CAUTION]
>  Das Festlegen der nächsten Anweisung bewirkt, dass der Programmzähler direkt zur neuen Position springt. Seien Sie daher vorsichtig, wenn Sie diesen Befehl verwenden.  
>   
>  -   Anweisungen zwischen den alten und neuen Ausführungspunkten werden nicht ausgeführt.  
> -   Wenn Sie den Ausführungspunkt rückwärts verschieben, werden dazwischenliegende Anweisungen nicht rückgängig gemacht.  
> -   Wenn Sie die nächste Anweisung in eine andere Funktion oder in einen anderen Gültigkeitsbereich verschieben, wird i. d. R. die Aufrufliste beeinträchtigt, wodurch ein Laufzeitfehler oder eine Ausnahme ausgelöst wird. Wenn Sie versuchen, die nächste Anweisung in einen anderen Gültigkeitsbereich zu verschieben, wird ein Dialogfenster mit einer Warnung geöffnet, in dem Sie den Vorgang abbrechen können. In Visual Basic können Sie die nächste Anweisung nicht in einen anderen Bereich oder in eine andere Funktion verlegen.  
> -   In systemeigenem C++-Code kann das Festlegen der nächsten Anweisung bei aktivierter Laufzeitprüfung dazu führen, dass am Ende der Methode eine Ausnahme ausgelöst wird.  
> -   Wenn die Funktion "Bearbeiten und Fortfahren" aktiviert ist, schlägt das Ausführen der Option **Nächste Anweisung festlegen** fehl, wenn Sie Änderungen vorgenommen haben, die von "Bearbeiten und Fortfahren" nicht sofort neu zugeordnet werden können. Dies kann auftreten, wenn Sie z. B. Code in einem catch-Block bearbeitet haben. In diesem Fall sehen Sie eine Fehlermeldung angezeigt, die mitteilt, dass der Vorgang nicht unterstützt.  
  
> [!NOTE]
>  In verwaltetem Code können Sie die nächste Anweisung unter den folgenden Bedingungen nicht verschieben:  
>   
>  -   Die nächste Anweisung und die aktuelle Anweisung befinden sich in verschiedenen Methoden.  
> -   Das Debuggen wurde über Just-In-Time-Debuggen gestartet.  
> -   Die Aufrufliste wird gerade entladen.  
> -   Eine System.StackOverflowException oder eine System.Threading.ThreadAbortException wurden ausgelöst.  
  
 Während die Anwendung aktiv ausgeführt wird, ist es nicht möglich, die nächste Anweisung festzulegen. Zum Festlegen der nächsten Anweisung muss sich der Debugger im Unterbrechungsmodus befinden.  
  
## <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Einzelschritt in Nichtbenutzercode  
 Der Debugger versucht standardmäßig, um Ihnen zu zeigen nur den app-Code während des Debuggens, der von einem Debugger Einstellung bestimmt wird *nur mein Code*. (Siehe [nur mein Code](../debugger/just-my-code.md) sehen, wie dies für verschiedene Projekttypen und Sprachen funktioniert und wie Sie das Verhalten anpassen können.) Allerdings manchmal während des Debuggens, möglicherweise möchten betrachten Frameworkcode, Drittanbieter-Bibliothekscode oder Aufrufe des Betriebssystems (Systemaufrufe).  
  
 Sie können nur mein Code deaktivieren, navigieren Sie zu **Tools** > **Optionen** > **Debuggen** , und deaktivieren Sie die **nur meinen Code aktivieren** Kontrollkästchen.  
  
 Wenn nur mein Code deaktiviert ist, wird der Debugger einen Einzelschritt in Nichtbenutzercode und Nichtbenutzercode in den Debuggerfenstern angezeigt wird.  
  
> [!NOTE]
>  Nur mein Code wird in Geräteprojekten nicht unterstützt.  
  
 **Schrittweise Ausführung von Systemaufrufen**  
  
 Wenn Sie Debugsymbole für den Systemcode geladen haben und nicht nur mein Code aktiviert ist, können Sie einen Systemaufruf ebenso wie jeden anderen Aufruf schrittweise.  
  
 Um Zugriff auf Microsoft-Symboldateien finden Sie unter [verwenden Sie Symbolserver, um Symboldateien nicht auf dem lokalen Computer zu suchen](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) in der [angeben von Symboldateien (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Thema.  
  
 So laden Sie Symbole für eine bestimmte Systemkomponente während des Debuggings:  
  
1.  Öffnen Sie das Fenster "Module" (Tastatur: **Strg + Alt + U**).  
  
2.  Wählen Sie das Modul aus, für das Sie Symbole laden möchten.  
  
     Sie können in der Spalte **Symbolstatus** feststellen, für welche Module Symbole geladen sind.  
  
3.  Wählen Sie im Kontextmenü die Option **Symbole laden** aus.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Schrittweise Ausführung von Eigenschaften und Operatoren in verwaltetem Code  
 Standardmäßig überspringt der Debugger die Eigenschaften und Operatoren in verwaltetem Code. In den meisten Fällen sorgt dies für einen besseren Debugvorgang. Um die schrittweise Ausführung von Eigenschaften oder Operatoren zu aktivieren, wählen Sie **Debuggen** > **Optionen**. Auf der **Debuggen** > **allgemeine** Seite löschen der **Eigenschaften und Operatoren (nur verwaltet) überspringen** Kontrollkästchen