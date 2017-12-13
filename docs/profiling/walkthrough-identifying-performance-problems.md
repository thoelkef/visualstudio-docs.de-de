---
title: 'Exemplarische Vorgehensweise: Identifizieren von Leistungsproblemen | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: "53"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d52f6bfe745cf7e8684094cf9244b6eedcba13a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-identifying-performance-problems"></a>Exemplarische Vorgehensweise: Identifizieren von Leistungsproblemen
In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie ein Profil einer Anwendung erstellt wird, um Leistungsprobleme zu erkennen.  
  
 In dieser exemplarischen Vorgehensweise werden Sie Schritt für Schritt durch den Vorgang der Profilerstellung einer verwalteten Anwendung geleitet, wobei mithilfe von Sampling und Instrumentierung Leistungsprobleme in der Anwendung isoliert und identifiziert werden.  
  
 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie die folgenden Schritte aus:  
  
-   Profilerstellung einer Anwendung mithilfe der Samplingmethode  
  
-   Analysieren der Ergebnisse der Profilerstellung, für die ein Sampling durchgeführt wurde, um ein Leistungsproblem zu lokalisieren und zu beheben  
  
-   Profilerstellung einer Anwendung mithilfe der Instrumentationsmethode  
  
-   Analysieren der Ergebnisse der Profilerstellung, für die eine Instrumentation durchgeführt wurde, um ein Leistungsproblem zu lokalisieren und zu beheben  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Grundlegende Kenntnisse über C#.  
  
-   Eine Kopie von [PeopleTrax-Beispiel](../profiling/peopletrax-sample-profiling-tools.md).  
  
 Um mit den durch die Profilerstellung bereitgestellten Informationen arbeiten zu können, sollten Symbolinformationen für das Debuggen verfügbar sein.  
  
## <a name="profiling-by-using-the-sampling-method"></a>Profilerstellung mithilfe der Samplingmethode  
 Das Sampling ist eine Methode der Profilerstellung, bei der der betreffende Prozess periodisch zum Bestimmen der aktiven Funktion überprüft wird. Die resultierenden Daten enthalten Angaben dazu, wie häufig die betreffende Funktion sich während des Samplings des Prozesses in der Aufrufliste ganz oben befunden hat.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>So führen Sie eine Profilerstellung einer Anwendung mithilfe der Samplingmethode aus  
  
1.  Öffnen Sie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] mit Administratorrechten. Die Ausführung als Administrator ist für die Profilerstellung erforderlich.  
  
2.  Öffnen Sie die Projektmappe "PeopleTrax".  
  
     Die Projektmappe PeopleTrax wird jetzt im Projektmappen-Explorer angezeigt.  
  
3.  Legen Sie die Einstellung für die Projektkonfiguration auf **Release** fest.  
  
     Verwenden Sie zum Ermitteln von Leistungsproblemen in der Anwendung nach Möglichkeit einen Releasebuild. Für die Profilerstellung wird ein Releasebuild empfohlen, da bei einem Debugbuild zusätzliche Informationen in den Build kompiliert werden, die die Leistung beeinträchtigen können. Leistungsprobleme werden daher möglicherweise nicht korrekt vermittelt.  
  
4.  Wählen Sie im Menü **Analysieren** die Option **Leistungsprofiler**, wählen Sie **Leistungs-Assistent**, und wählen Sie dann **Starten**.  
  
     Der Leistungs-Assistent wird angezeigt.  
  
5.  Vergewissern Sie sich, dass **CPU-Sampling (empfohlen)** ausgewählt ist, und klicken Sie anschließend auf **Weiter**.  
  
6.  Wählen Sie unter **Welche Anwendung soll für die Profilerstellung als Ziel festgelegt werden** die Option „PeopleTrax“ aus, und klicken Sie auf **Weiter**.  
  
     Das Projekt wird von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] erstellt, und die Profilerstellung für die Anwendung wird gestartet. Das Anwendungsfenster für **PeopleTrax** wird angezeigt.  
  
7.  Klicken Sie auf **Get People** (Personen abrufen).  
  
8.  Klicken Sie auf **Daten exportieren**.  
  
     In Editor wird eine neue Datei angezeigt, die die exportierten Daten aus **PeopleTrax** enthält.  
  
9. Schließen Sie Editor, und schließen Sie dann die Anwendung **PeopleTrax**.  
  
     Der Profiler generiert eine Profilerstellungs-Datendatei (\*.vsp-Datei), führt den Dateinamen im Abschnitt „Berichte“ des Fensters „Leistungs-Explorer“ auf und lädt im Hauptfenster von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] automatisch die Ansicht **Zusammenfassung** für die Datendatei.  
  
#### <a name="to-analyze-sampled-profiling-results"></a>So analysieren Sie die Ergebnisse der Profilerstellung, für die ein Sampling durchgeführt wurde  
  
1.  Die Ansicht „Zusammenfassung“ enthält eine Zeitachse mit der CPU-Auslastung für den Zeitraum der Profilerstellung, die Liste **Langsamster Pfad**, die die aktivste Verzweigung der Aufrufstruktur der Anwendung darstellt, sowie die Liste **Funktionen, die die meisten Einzelaufgaben durchführen** mit den Funktionen, die beim Ausführen des Codes im eigenen Funktionstext am stärksten gesampelt wurden.  
  
     Überprüfen Sie die Liste **Langsamster Pfad**, und beachten Sie, dass es sich bei der Methode „PeopleNS.People.GetNames“ um die PeopleTrax-Funktion handelt, die dem Ende der Liste am nächsten ist. Aufgrund dieser Position eignet sich das Element besonders gut für eine Analyse. Klicken Sie auf den Funktionsnamen, um in der Ansicht **Funktionsdetails** Details zu „GetNames“ anzuzeigen.  
  
2.  Die Ansicht **Funktionsdetails** enthält zwei Fenster. Das Fenster "Kostenverteilung" enthält eine grafische Darstellung der ausgeführten Aufgaben der Funktion, eine Darstellung der Aufgaben, die von den aufgerufenen Funktionen ausgeführt wurden, sowie eine Darstellung des Beitrags von Funktionen, von denen die Funktion aufgerufen wurde, zur Anzahl der gesampelten Instanzen. Durch Klicken auf einen Funktionsnamen können Sie die Funktion ändern, die sich im Fokus der Ansicht befindet. So können Sie beispielsweise auf "PeopleNS.People.GetPeople" klicken, um die Funktion "GetPeople" auszuwählen.  
  
     Das Fenster **Funktionscodeansicht** enthält den Quellcode für die Funktion (sofern verfügbar). Darüber hinaus werden die speicherintensivsten Zeilen in der ausgewählten Funktion hervorgehoben. Ist "GetNames" ausgewählt, ist zu sehen, dass von dieser Funktion eine Zeichenfolge aus den Anwendungsressourcen gelesen wird und die einzelnen Zeilen in der Zeichenfolge anschließend mithilfe von <xref:System.IO.StringReader> einer <xref:System.Collections.ArrayList> hinzugefügt werden. Diese Funktion kann offenbar nicht optimiert werden.  
  
3.  Da es sich bei "PeopleNS.People.GetPeople" um den einzigen Aufrufer von "GetNames" handelt, klicken Sie im Fenster "Kostenverteilung" auf "GetPeople", um den Code zu untersuchen. Von dieser Methode wird eine <xref:System.Collections.ArrayList> mit PersonInformationNS.PersonInformation-Objekten aus den Namen der Personen und Unternehmen zurückgegeben, die von "GetNames" erstellt wurden. "GetNames" wird jedoch bei jeder Erstellung des PersonInformation-Objekts zweimal aufgerufen. Wie Sie sehen, lässt sich die Methode auf einfache Weise optimieren, indem die Listen lediglich einmal beim Start der Methode erstellt und während der PersonInformation-Erstellungsschleife indiziert werden.  
  
4.  Im Code der Beispielanwendung ist eine alternative Version von "GetPeople" enthalten. Fügen Sie den Buildeigenschaften ein Symbol für die bedingte Kompilierung hinzu, um die optimierte Funktion aufzurufen. Klicken Sie im Fenster „Projektmappen-Explorer“ mit der rechten Maustaste auf das Projekt „People“, und klicken Sie anschließend auf **Eigenschaften**. Klicken Sie im Menü der Eigenschaftenseite auf **Erstellen**, und geben Sie anschließend im Textfeld „Conditional compilation symbol“ (Symbol für bedingte Kompilierung) den Text **OPTIMIZED_GETPEOPLE** ein. Im nächsten Build wird die ursprüngliche Methode durch die optimierte Version von "GetPeople" ersetzt.  
  
5.  Führen Sie die Leistungssitzung erneut aus. Klicken Sie auf der Symbolleiste des Leistungs-Explorers auf **Mit Profilerstellung starten**. Klicken Sie auf **Get People** (Personen abrufen) und anschließend auf **Daten exportieren**. Schließen Sie das angezeigte Editor-Fenster und anschließend die Anwendung "PeopleTrax".  
  
     Eine neue Profilerstellungs-Datendatei wird generiert, und im Hauptfenster von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] wird eine **Zusammenfassung** für die neuen Daten angezeigt.  
  
6.  Wählen Sie zum Vergleichen der beiden Profilerstellungen im Leistungs-Explorer die beiden Datendateien aus, klicken Sie mit der rechten Maustaste auf die Dateien, und klicken Sie anschließend auf **Leistungsberichte vergleichen**. Im Hauptfenster von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] wird ein Fenster mit einem Vergleichsbericht angezeigt. Die Spalte **Delta** enthält die Änderung des Leistungswerts der Funktionen vom früheren **Baselinewert** zum späteren **Vergleichswert**. Die zu vergleichenden Werte können in der Dropdownliste **Spalte** ausgewählt werden. Wählen Sie **Inklusive Samplings in %** aus.  
  
     Beachten Sie, dass bei der GetPeople-Methode und der GetNames-Methode eine beträchtliche Leistungssteigerung zu verzeichnen ist.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>Profilerstellung mithilfe der Instrumentationsmethode  
 Bei der Instrumentation handelt es sich um eine Profilerstellungsmethode, bei der vom Profiler Testfunktionen in speziell erstellte Versionen der Binärdateien eingefügt werden, für die das Profil erstellt wird. Von den Testfunktionen werden am Start und am Ende von Funktionen in den instrumentierten Modulen sowie an allen Aufrufsites in diesen Funktionen Zeitsteuerungsinformationen gesammelt. Der Instrumentationsprozess ist hilfreich beim Untersuchen von Problemen mit Eingabe-/Ausgabeoperationen wie dem Schreiben auf einen Datenträger oder der Kommunikation in einem Netzwerk. Bei der Instrumentation erhalten Sie zwar ausführlichere Informationen als beim Sampling, dafür wird jedoch stärker in die Prozessausführung eingegriffen, und auch der Mehraufwand fällt höher aus. Instrumentierte Binärdateien sind zudem größer als Binärdateien für eine Debug- oder Releaseversion und nicht für die Bereitstellung vorgesehen.  
  
 In diesem Abschnitt der exemplarischen Vorgehensweise wird in der Anwendung "PeopleTrax", für die bereits zuvor eine Profilerstellung ausgeführt wurde, mithilfe der Instrumentationsmethode weiterer optimierbarer Code gesucht. Mithilfe des Filters der Zeitachse in der Zusammenfassungsansicht wird die Analyse auf das Exportdatenszenario der Anwendung konzentriert, für die ein Profil erstellt wurde und in der eine Liste mit Personen in eine Editor-Datei geschrieben wird.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>So führen Sie eine Profilerstellung einer vorhandenen Anwendung mithilfe der Instrumentationsmethode durch  
  
1.  Öffnen Sie ggf. die Anwendung "PeopleTrax" in Visual Studio.  
  
     Vergewissern Sie sich, dass Sie als Administrator angemeldet sind und die Buildkonfiguration für die Projektmappe auf **Release** festgelegt ist.  
  
2.  Klicken Sie im Leistungs-Explorer auf **Instrumentierung**.  
  
3.  Klicken Sie auf der Symbolleiste des Leistungs-Explorers auf **Mit Profilerstellung starten**.  
  
     Das Projekt wird erstellt, und die Profilerstellung der Anwendung wird gestartet. Das Anwendungsfenster für "PeopleTrax" wird angezeigt.  
  
4.  Klicken Sie auf **Get People** (Personen abrufen).  
  
     Im Datenblatt PeopleTrax werden Daten angezeigt.  
  
5.  Warten Sie etwa 10 Sekunden, und klicken Sie anschließend auf **Daten exportieren**.  
  
     In **Editor** wird eine neue Datei angezeigt, die eine Liste der Personen aus PeopleTrax enthält. Durch das Warten lässt sich die Datenexportprozedur für die Filterung leichter identifizieren.  
  
6.  Schließen Sie **Editor**, und schließen Sie dann die Anwendung **PeopleTrax**.  
  
     [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] generiert einen Bericht über die Leistungssitzung (* .vsp).  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>So analysieren Sie die Ergebnisse der instrumentierten Profilerstellung  
  
1.  Das Zeitachsendiagramm der Ansicht **Zusammenfassung** des Berichts enthält die CPU-Auslastung des Programms während der Profilerstellung. Bei dem Exportvorgang der Daten muss es sich um die große Spitze oder den Ausschlag rechts im Diagramm handeln. Die Leistungssitzung kann gefiltert werden, um nur die Daten anzuzeigen und zu analysieren, die im Rahmen des Exportvorgangs erfasst wurden. Klicken Sie im Diagramm auf eine Position links des Punkts, an dem der Exportvorgang der Daten beginnt. Klicken Sie auf eine Position rechts des Vorgangs. Klicken Sie anschließend rechts neben der Zeitachse in der Liste mit den Links auf **Nach Auswahl filtern**.  
  
     In der Struktur **Langsamster Pfad** wird ersichtlich, dass die <xref:System.String.Concat%2A>-Methode, die von der PeopleTrax.Form1.ExportData-Methode aufgerufen wird, sehr zeitaufwändig ist. Da sich **System.String.Concat** auch am Anfang der Liste **Funktionen mit den meisten einzelnen Aufgaben** befindet, stellt eine Verringerung der für die Funktion aufgewendeten Zeit mit großer Wahrscheinlichkeit eine Optimierung dar.  
  
2.  Doppelklicken Sie in einer der Zusammenfassungstabellen auf **System.String.Concat**, um in der Ansicht „Funktionsdetails“ weitere Informationen anzuzeigen.  
  
3.  Wie Sie sehen, ist "PeopleTrax.Form1.ExportData" die einzige Methode, von der "Concat" aufgerufen wird. Klicken Sie in der Liste **Aufrufende Funktionen** auf **PeopleTrax.Form1.ExportData**, um die Methode als Ziel der Ansicht „Funktionsdetails“ auszuwählen.  
  
4.  Untersuchen Sie die Methode im Fenster "Funktionscodeansicht". Beachten Sie, dass es keine literalen Aufrufe von **System.String.Concat** gibt. Stattdessen wird mehrmals der Operand „+=“ verwendet, der vom Compiler durch Aufrufe von **System.String.Concat** ersetzt wird. Änderungen an einer Zeichenfolge in .NET Framework führen dazu, dass eine neue Zeichenfolge zuordnet wird. .NET Framework enthält eine <xref:System.Text.StringBuilder>-Klasse, die für die Zeichenfolgenverkettung optimiert ist.  
  
5.  Um diesen Problembereich durch optimierten Code zu ersetzen, fügen Sie dem Projekt PeopleTrax OPTIMIZED_EXPORTDATA als Symbol für die bedingte Kompilierung hinzu.  
  
6.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt „PeopleTrax“, und klicken Sie dann auf **Eigenschaften**.  
  
     Das Eigenschaftenformular des Projekts PeopleTrax wird angezeigt.  
  
7.  Klicken Sie auf die Registerkarte **Erstellen**.  
  
8.  Geben Sie im Textfeld **Symbole für bedingte Kompilierung** den Text **OPTIMIZED_EXPORTDATA** ein.  
  
9. Schließen Sie das Eigenschaftenformular des Projekts, und wählen Sie **Alle speichern** aus, wenn Sie dazu aufgefordert werden.  
  
 Wenn Sie die Anwendung erneut ausführen, stellen Sie bei der Leistung merkliche Verbesserungen fest. Es wird empfohlen, die Profilerstellungssitzung auch dann erneut auszuführen, wenn sich in der Leistung für den Benutzer erkennbare Verbesserungen eingestellt haben. Der erneute Review der Daten nach Behebung eines Problems ist überaus wichtig, da unter Umständen noch andere Probleme vorhanden sind, die aufgrund des ersten Problems nicht ersichtlich waren.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersichten](../profiling/overviews-performance-tools.md)   
 [Erste Schritte](../profiling/getting-started-with-performance-tools.md)   
 [/Z7, /Zi, /ZI (Debuginformationsformat)](/cpp/build/reference/z7-zi-zi-debug-information-format)