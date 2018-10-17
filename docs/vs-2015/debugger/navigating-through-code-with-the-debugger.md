---
title: Navigieren im Code mit dem Debugger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d91d99b6eaa33f3aae84ecd3510bf08fe194f101
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186159"
---
# <a name="navigating-through-code-with-the-debugger"></a>Navigieren im Code mit dem Debugger
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Befehlen und Tastenkombinationen zum Navigieren im Code im Debugger vertraut machen und veranlasst, die sie schneller und einfacher zu finden und beheben Sie Probleme in Ihrer app. Während Sie Code im Debugger navigieren, können Sie [untersuchen Sie den Status Ihrer App](https://msdn.microsoft.com/library/mt243867.aspx#BKMK_Inspect_Variables) oder erfahren Sie mehr über die Ausführungsablauf.  
  
## <a name="start-debugging"></a>Debugging starten  
 Häufig, die Sie starten eine Debugsitzung mithilfe **F5** (**Debuggen** / **Debuggen starten**). Dieser Befehl startet Ihre app mit dem angefügten Debugger.  
  
 Der grüne Pfeil wird auch der Debugger gestartet (identisch mit **F5**).  
  
 ![DBG&#95;Basics&#95;Start&#95;Debugging](../debugger/media/dbg-basics-start-debugging.png "DBG_Basics_Start_Debugging")  
  
 Weitere Möglichkeiten, dass Sie die app, mit dem angefügten Debugger starten können enthalten **F11** ([Einzelschritte in Code](#BKMK_Step_into__over__or_out_of_the_code)), **F10** ([überspringen](#BKMK_Step_over_Step_out)), oder Mithilfe von **Ausführen bis Cursor**.  Finden Sie unter den anderen Abschnitten in diesem Thema Informationen, in denen Sie diese Optionen.  
  
 Beim Debuggen zeigt die gelbe Linie Sie den Code, der als Nächstes ausgeführt wird.  
  
 ![DBG&#95;Basics&#95;Break&#95;Mode](../debugger/media/dbg-basics-break-mode.png "DBG_Basics_Break_Mode")  
  
 Während des Debuggens können Sie zwischen Befehlen wie wechseln **F5**, **F11** und andere Funktionen in diesem Thema (z. B. Haltepunkte) beschrieben werden, sodass schnell auf den Code zu betrachten.  
  
 Die meisten Debuggerfunktionen, z. B. Anzeigen der Variablenwerte im Lokalfenster oder Auswerten von Ausdrücken im Überwachungsfenster, stehen nur während der Debugger angehalten ist (so genannte *Unterbrechungsmodus*). Wenn der Debugger angehalten wird, der app-Status wird angehalten, während der Funktionen, Variablen und Objekte im Speicher verbleiben. Während Sie sich im Unterbrechungsmodus befindet, können Sie die Elemente-Positionen und Zustände, um nach Verstößen oder Fehlern zu suchen untersuchen. Bei einigen Projekttypen können Sie auch die app im Unterbrechungsmodus Anpassungen vornehmen.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Einzelschritt in Code Zeile für Zeile  
 Verwenden Sie zum Beenden auf jede Codezeile (jede Anweisung) während des Debuggens die **F11** Tastenkombination (oder **Debuggen** / **Einzelschritt** im Menü).  
  
> [!TIP]
>  Wie Sie jede Codezeile ausführen, können Sie Variablen, deren Werte angezeigt werden soll, oder verwenden Sie zeigen die ["lokal"](../debugger/autos-and-locals-windows.md) und [Überwachen](../debugger/autos-and-locals-windows.md) Windows überwachen Sie ihre Werte ändern.  
  
 Hier sind einige Details über das Verhalten des **Einzelschritt**:  
  
-   Bei einem geschachtelten Funktionsaufruf führt **Einzelschritt** die am tiefsten geschachtelte Funktion in Einzelschritten aus. Wenn Sie **Einzelschritt** für einen Aufruf wie `Func1(Func2())`verwenden, führt der Debugger die Funktion `Func2`in Einzelschritten aus.  
  
-   Der Debugger durchläuft tatsächlich durch Codeanweisungen anstatt durch physische Zeilen. Beispielsweise kann eine `if` -Klausel in eine Zeile geschrieben werden:  
  
    ```csharp  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```vb  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Wenn Sie einen Einzelschritt in diese Zeile ausführen, behandelt der Debugger die Bedingung als einen Schritt und das Ergebnis als anderen Schritt (in diesem Beispiel lautet die Bedingung "true").  
  
 Um die Aufrufliste während der schrittweisen visuell zu verfolgen, finden Sie unter [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Step_over_Step_out"></a> Code, wird übersprungen, Funktionen schrittweise durchlaufen  
 Wenn der Code im Debugger ausgeführt wird, oft Sie feststellen, dass Sie nicht sehen, was passiert, in einer bestimmten Funktion müssen (nicht wichtig es oder Sie wissen es funktioniert, wie gut getestete Bibliothekscode). Mit diesen Befehlen können Sie um mithilfe von Code zu überspringen (die Funktionen weiterhin auszuführen, natürlich, aber der Debugger überspringt diese).  
  
|Tastenkombination|Menübefehl|Beschreibung|  
|----------------------|------------------|-----------------|  
|**F10**|**Prozedurschritt**|Wenn die aktuelle Zeile einen Funktionsaufruf enthält **Prozedurschritt** führt den Code, und klicken Sie dann in der ersten Zeile des Codes angehalten, wenn die aufgerufene Funktion zurückkehrt.|  
|**UMSCHALT+F11**|**Ausführen bis Rücksprung**|**Ausführen bis Rücksprung** wird weiter ausgeführt, Code und hält die Ausführung bei Rückgabe von der aktuelle Funktion (der Debugger überspringt über die aktuelle Funktion).|  
  
> [!TIP]
>  Wenn Sie den Einstiegspunkt in Ihrer app finden möchten, beginnen Sie mit **F10** oder **F11**. Diese Befehle sind häufig hilfreich, wenn Sie den app-Status überprüfen oder versuchen, Weitere Informationen zu der Ausführungsablauf.  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Führen Sie bis zu einer bestimmten Position oder Funktion aus  
 Häufig die bevorzugte Methode für das Debuggen von Code diese Methoden sind hilfreich, wenn man genau, welchen Code Sie überprüfen möchten, oder mindestens Sie wissen, in dem Sie debuggen möchten.  
  
-   **Festlegen von Haltepunkten im Code**  
  
     Um einen einfachen Haltepunkt im Code festzulegen, öffnen Sie die Quellcodedatei im Visual Studio-Editor. Setzen Sie den Cursor auf die Zeile des Codes, wo Sie möchten unterbrechen die Ausführung aus, und klicken Sie dann mit der rechten Maustaste im Codefenster "finden im Kontextmenü und wählen Sie **Haltepunkt / Haltepunkt einfügen** (oder drücken Sie **F9**). Der Debugger hält die Ausführung rechts, bevor die Zeile ausgeführt wird.  
  
     ![Festlegen eines Haltepunkts](../debugger/media/dbg-basics-setbreakpoint.png "DBG_Basics_SetBreakpoint")  
  
     Haltepunkte in Visual Studio bieten einen umfangreichen Satz von zusätzlichen Funktionen, wie z. B. bedingte Haltepunkte und Ablaufverfolgungspunkte. Finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md).  
  
-   **Ausführen bis zur Cursorplatzierung**  
  
     Um den Code bis zur Cursorposition auszuführen, platzieren Sie den Cursor in einem Quellcodefenster auf eine ausführbare Codezeile. Wählen Sie auf die Anmerkung der Redaktion im Kontextmenü (Rechtsklick im Editor) **Ausführen bis Cursor**. Dies entspricht dem Festlegen als temporären Haltepunkts.  
  
-   **Manuelles Unterbrechen im Code**  
  
     Um die Ausführung einer Anwendung in der nächsten verfügbaren Codezeile zu unterbrechen, wählen Sie **Debuggen**, **Alle unterbrechen** (Tastatur: **Ctrl+Alt+Break**).  
  
     Wenn Sie die Ausführung von Code ohne zugehörige Quell- oder Symboldateien (PDB-Dateien) unterbrechen, wird im Debugger die Seite **Die Quelldatei wurde nicht gefunden** oder **Symbol nicht gefunden** geöffnet, auf der Sie die entsprechenden Dateien suchen können. Weitere Informationen finden Sie unter [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Wenn Sie nicht auf die zugehörigen Hilfsdateien zugreifen können, können Sie dennoch die Assemblyanweisungen im Disassemblyfenster debuggen.  
  
-   **Ausführen bis zu einer Funktion in der Aufrufliste**  
  
     In der **Aufrufliste** Fenster (während des Debuggens verfügbar), wählen Sie die Funktion, mit der rechten Maustaste und wählen Sie **Ausführen bis Cursor**. Um die Aufrufliste visuell zu verfolgen, finden Sie unter [Zuordnen von Methoden in der Aufrufliste beim Debuggen](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
-   **Ausführen bis zu einer Funktion anhand des Namens**  
  
     Sie können feststellen, dass den Debugger die Anwendung ausgeführt wird, bis eine bestimmte Funktion erreicht. Sie können die Funktion anhand ihres Namens angeben oder in der Aufrufliste auswählen.  
  
     Um eine Funktion anhand des Namens anzugeben, wählen Sie **Debuggen**, **Neuer Haltepunkt**, **Halten bei Funktion**aus, und geben Sie dann den Namen der Funktion und andere Identifikationsinformationen ein.  
  
     ![Dialogfeld ' neue Haltepunkt](../debugger/media/dbg-execution-newbreakpoint.png "DBG_Execution_NewBreakpoint")  
  
     Wenn die Funktion überladen ist oder sich in mehreren Namespaces befindet, können Sie die gewünschten Funktionen im Dialogfeld **Haltepunkte wählen** auswählen.  
  
     ![Wählen Sie im Dialogfeld Breakpoints](../debugger/media/dbg-execution-overloadedbreakpoints.png "DBG_Execution_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Bewegen Sie den Mauszeiger, um den Ausführungsfluss zu ändern.  
 Während der Debugger angehalten wird, können Sie den Anweisungszeiger Festlegen der nächsten Anweisung der Ausführung von Code verschieben. Die Position der nächsten auszuführenden Anweisung wird durch eine gelbe Pfeilspitze am Rand eines Quellcodefensters oder Disassemblierungsfensters markiert. Durch das Verschieben dieser Pfeilspitze können Sie einen Teil des Codes überspringen oder zu einer bereits ausgeführten Zeile zurückkehren. Dies ist zum Beispiel sinnvoll, um einen Codeabschnitt zu überspringen, von dem bereits bekannt ist, dass er einen Fehler enthält.  
  
 !["Example2"](../debugger/media/dbg-basics-example2.png "DBG_Basics_Example2")  
  
 Zum Festlegen der nächsten auszuführenden Anweisung verwenden Sie eines der folgenden Verfahren:  
  
-   Ziehen Sie die gelbe Pfeilspitze in einem Quellcodefenster in derselben Quelldatei an die Position, an der Sie die nächste Anweisung festlegen möchten.  
  
-   Setzen Sie den Cursor in einem Quellcodefenster in der Zeile, die Sie als Nächstes ausführen, mit der rechten Maustaste, und wählen möchten **Festlegen der nächsten Anweisung**.  
  
-   Setzen Sie den Cursor im dissamblyfenster auf die Assemblyanweisung, die Sie verwenden möchten, führen Sie als Nächstes der rechten Maustaste auf ein, und wählen Sie **Festlegen der nächsten Anweisung**.  
  
> [!CAUTION]
>  Das Festlegen der nächsten Anweisung bewirkt, dass der Programmzähler direkt zur neuen Position springt. Seien Sie daher vorsichtig, wenn Sie diesen Befehl verwenden.  
>   
>  -   Anweisungen zwischen den alten und neuen Ausführungspunkten werden nicht ausgeführt.  
> -   Wenn Sie den Ausführungspunkt rückwärts verschieben, werden dazwischenliegende Anweisungen nicht rückgängig gemacht.  
> -   Wenn Sie die nächste Anweisung in eine andere Funktion oder in einen anderen Gültigkeitsbereich verschieben, wird i. d. R. die Aufrufliste beeinträchtigt, wodurch ein Laufzeitfehler oder eine Ausnahme ausgelöst wird. Wenn Sie versuchen, die nächste Anweisung in einen anderen Gültigkeitsbereich zu verschieben, wird ein Dialogfenster mit einer Warnung geöffnet, in dem Sie den Vorgang abbrechen können. In Visual Basic können Sie die nächste Anweisung nicht in einen anderen Bereich oder in eine andere Funktion verlegen.  
> -   In systemeigenem C++-Code kann das Festlegen der nächsten Anweisung bei aktivierter Laufzeitprüfung dazu führen, dass am Ende der Methode eine Ausnahme ausgelöst wird.  
> -   Wenn die Funktion "Bearbeiten und Fortfahren" aktiviert ist, schlägt das Ausführen der Option **Nächste Anweisung festlegen** fehl, wenn Sie Änderungen vorgenommen haben, die von "Bearbeiten und Fortfahren" nicht sofort neu zugeordnet werden können. Dies kann auftreten, wenn Sie z. B. Code in einem catch-Block bearbeitet haben. Dann wird die Fehlermeldung angezeigt, dass der Vorgang nicht unterstützt wird.  
  
> [!NOTE]
>  In verwaltetem Code können Sie die nächste Anweisung unter den folgenden Bedingungen nicht verschieben:  
>   
>  -   Die nächste Anweisung und die aktuelle Anweisung befinden sich in verschiedenen Methoden.  
> -   Das Debuggen wurde über Just-In-Time-Debuggen gestartet.  
> -   Die Aufrufliste wird gerade entladen.  
> -   Eine System.StackOverflowException oder eine System.Threading.ThreadAbortException wurden ausgelöst.  
  
 Während die Anwendung aktiv ausgeführt wird, ist es nicht möglich, die nächste Anweisung festzulegen. Zum Festlegen der nächsten Anweisung muss sich der Debugger im Unterbrechungsmodus befinden.  
  
## <a name="step-into-non-user-code"></a>Nicht-benutzerseitiger Code in Einzelschritten ausführen  
 Der Debugger versucht standardmäßig, soll veranschaulicht werden, die von einem Debugger, die Einstellung bestimmt wird nur Ihr app-Code während des Debuggens *nur mein Code*. (Finden Sie unter [nur mein Code](../debugger/just-my-code.md) angezeigt, wie dies für verschiedene Projekttypen und Sprachen funktioniert und wie Sie das Verhalten anpassen können.) Jedoch manchmal während des Debuggens, Sie möchten Betrachten der Framework-Code, Code für Bibliotheken von Drittanbietern oder Aufrufe des Betriebssystems (Systemaufrufe).  
  
 Sie können nur mein Code deaktivieren, indem Sie zu **Tools** / **Optionen** / **Debuggen** und deaktivieren Sie die **nur meinen Code aktivieren** Kontrollkästchen.  
  
 Wenn nur mein Code deaktiviert ist, der Debugger einen Einzelschritt in nicht-benutzerseitigen Code und nicht-benutzerseitigen Code wird in den Debuggerfenstern angezeigt.  
  
> [!NOTE]
>  Nur mein Code wird in Geräteprojekten nicht unterstützt.  
  
 **Schrittweise Ausführung von Systemaufrufen**  
  
 Wenn Sie Debugsymbole für den Systemcode geladen haben, und nicht nur mein Code aktiviert ist, können Sie einen Systemaufruf ebenso wie jeden anderen Aufruf schrittweise.  
  
 Um Zugriff auf Microsoft-Symboldateien finden Sie unter [Verwenden von Symbolservern zum Suchen von Symboldateien nicht auf dem lokalen Computer](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) in die [angeben von Symbol (.pdb) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Thema.  
  
 So laden Sie Symbole für eine bestimmte Systemkomponente während des Debuggings:  
  
1.  Öffnen Sie das Fenster "Module" (Tastatur: **Ctrl+Alt+U**).  
  
2.  Wählen Sie das Modul aus, für das Sie Symbole laden möchten.  
  
     Sie können in der Spalte **Symbolstatus** feststellen, für welche Module Symbole geladen sind.  
  
3.  Wählen Sie im Kontextmenü die Option **Symbole laden** aus.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Schrittweise Ausführung von Eigenschaften und Operatoren in verwaltetem Code  
 Standardmäßig überspringt der Debugger die Eigenschaften und Operatoren in verwaltetem Code. In den meisten Fällen sorgt dies für einen besseren Debugvorgang. Wählen Sie zum Aktivieren von Eigenschaften oder Operatoren schrittweise **Debuggen** / **Optionen**. Deaktivieren Sie auf der Seite **Debuggen** / **Allgemein** das Kontrollkästchen **Eigenschaften und Operatoren überspringen (nur verwaltet)** .





