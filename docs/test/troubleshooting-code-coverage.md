---
title: Problembehandlung bei der Code Coverage | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 11
ms.author: douge
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 670fb2cb0d0c5b6aa954f5c4c02154c397ec4944
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshooting-code-coverage"></a>Problembehandlung bei der Code Coverage
Mit dem Tool zur Code Coverage-Analyse in Visual Studio werden Daten für native und verwaltete Assemblys (DLL- oder EXE-Dateien) erfasst. In einigen Fällen wird im Fenster "Codeabdeckungsergebnisse" jedoch ein Fehler ähnlich dem Folgenden angezeigt: "Es wurden leere Ergebnisse generiert: ..." Es gibt mehrere mögliche Gründe dafür, dass dies geschehen kann. Dieses Thema soll Ihnen helfen, diese Probleme zu beheben.  
  
## <a name="what-you-should-see"></a>Anzeige im Normalfall  
 Wenn Sie Im Menü „Test“ den Befehl **Code Coverage analysieren** auswählen und der Buildvorgang sowie die Tests erfolgreich ausgeführt werden, sollte im Fenster „Code Coverage“ eine Ergebnisliste angezeigt werden. Sie müssen möglicherweise die Elemente erweitern, um die Details anzuzeigen.  
  
 ![Code Coverage-Ergebnisse mit Färbung](../test/media/codecoverage1.png "CodeCoverage1")  
  
 Weitere Informationen finden Sie unter [Using Code Coverage to Determine How Much Code is being Tested (Wie Sie feststellen können, wie viel Code untersucht wird)](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Mögliche Gründe dafür, dass keine oder alte Ergebnisse angezeigt werden  
  
### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Verwenden Sie die richtige Edition von Visual Studio?  
 Sie benötigen Visual Studio Enterprise.  
  
### <a name="no-tests-were-executed"></a>Es wurden keine Tests ausgeführt.  
 Analyse  
 Überprüfen Sie das Ausgabefenster. Wählen Sie in der Dropdownliste **Ausgabe anzeigen von** die Option **Tests** aus. Überprüfen Sie, ob Warnungen oder Fehler protokolliert wurden.  
  
 Erklärung  
 Die Codeabdeckungsanalyse wird während der Tests ausgeführt. Sie schließt nur Assemblys ein, die während der Tests in den Arbeitsspeicher geladen werden. Wenn kein Test ausgeführt wird, gibt es nichts zur Codeabdeckung zu berichten.  
  
 Auflösung  
 Wählen Sie im Test-Explorer **Alle ausführen** aus, um zu überprüfen, ob die Tests erfolgreich ausgeführt werden. Beheben Sie alle Fehler, bevor Sie **Code Coverage analysieren** verwenden.  
  
### <a name="youre-looking-at-a-previous-result"></a>Sie sehen sich ein vorheriges Ergebnis an.  
 Wenn Sie die Tests ändern und erneut ausführen, können das vorherige Codeabdeckungsergebnis und die Codefarbe der alten Ausführung noch sichtbar sein.  
  
1.  Führen Sie "Codeabdeckung analysieren" aus.  
  
2.  Überprüfen Sie, ob Sie das aktuelle Resultset im Fenster "Codeabdeckungsergebnisse" ausgewählt haben.  
  
### <a name="pdb-symbol-files-are-unavailable"></a>PDB-Dateien (Symboldateien) sind nicht verfügbar  
 Analyse  
 Öffnen Sie den Zielordner für die Kompilierung (normalerweise "bin\debug"), und überprüfen Sie, ob für jede Assembly eine PDB-Datei im gleichen Verzeichnis vorhanden ist, in dem sich die DLL- oder EXE-Datei befindet.  
  
 Erklärung  
 Für das Codeabdeckungsmodul muss während des Testlaufs für jede Assembly der Zugriff auf die zugeordnete PDB-Datei möglich sein. Wenn für eine bestimmte Assembly keine PDB-Datei zur Verfügung steht, wird sie nicht analysiert.  
  
 Die PDB-Datei und die DLL- oder EXE-Datei müssen im selben Buildvorgang generiert werden.  
  
 Auflösung  
 Stellen Sie sicher, dass die Buildeinstellungen so konfiguriert sind, dass die PDB-Datei generiert wird. Wenn die PDB-Dateien beim Erstellen des Projekts nicht aktualisiert werden, öffnen Sie die Projekteigenschaften, wählen Sie die Seite **Build** aus, wählen Sie **Erweitert** aus, und überprüfen Sie **Debuginformationen**.  
  
 Wenn sich die PDB-Datei und die DLL- oder EXE-Datei an verschiedenen Speicherorten befinden, kopieren Sie die PDB-Datei in dasselbe Verzeichnis. Es ist auch möglich, das Code Coverage-Modul so zu konfigurieren, dass an anderen Speicherorten nach PDB-Dateien gesucht wird. Weitere Informationen finden Sie unter [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).  
  
### <a name="using-an-instrumented-or-optimized-binary"></a>Verwenden einer instrumentierten oder optimierten Binärdatei  
 Analyse  
 Stellen Sie fest, ob die Binärdatei einer erweiterten Optimierung unterzogen wurde, beispielsweise einer profilgesteuerten Optimierung, oder durch ein Profilerstellungstool wie "vsinstr.exe" oder "vsperfmon.exe" instrumentiert wurde.  
  
 Erklärung  
 Wenn eine Assembly bereits durch ein anderes Profilerstellungstool instrumentiert oder optimiert wurde, wird die Assembly bei der Codeabdeckungsanalyse nicht berücksichtigt.  
  
 Die Codeabdeckungsanalyse kann für solche Assemblys nicht ausgeführt werden.  
  
 Auflösung  
 Deaktivieren Sie die Optimierung, und verwenden Sie einen neuen Build.  
  
### <a name="code-is-not-managed-net-or-native-c-code"></a>Code ist kein verwalteter (.NET) oder systemeigener Code (C++)  
 Analyse  
 Überprüfen Sie, ob die Tests für verwalteten oder C++-Code ausgeführt werden.  
  
 Erklärung  
 Die Codeabdeckungsanalyse in Visual Studio steht nur für verwalteten und systemeigenen Code (C++) zur Verfügung. Wenn Sie mit Tools von Drittanbietern arbeiten, wird ein Teil des Codes oder der gesamte Code möglicherweise auf einer anderen Plattform ausgeführt.  
  
 Auflösung  
 Nicht verfügbar  
  
### <a name="assembly-has-been-installed-by-ngen"></a>Assembly wurde durch NGen installiert  
 Analyse  
 Stellen Sie sicher, dass die Assembly nicht aus dem systemeigenen Imagecache geladen wird.  
  
 Erklärung  
 Systemeigene Imageassemblys werden aus Leistungsgründen nicht analysiert. Weitere Informationen finden Sie unter [Ngen.exe (Native Image Generator)](http://msdn.microsoft.com/Library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).  
  
 Auflösung  
 Verwenden Sie eine MSIL-Version der Assembly. Verarbeiten Sie sie nicht mit NGen.  
  
### <a name="custom-runsettings-file-with-bad-syntax"></a>Benutzerdefinierte Datei ".runsettings" mit ungültiger Syntax  
 Analyse  
 Wenn Sie eine benutzerdefinierte Datei ".runsettings" verwenden, kann sie einen Syntaxfehler enthalten.  
  
 Dies führt dazu, dass keine Codeabdeckungsanalyse ausgeführt wird. Entweder wird das Fenster "Codeabdeckung" am Ende des Testlaufs nicht geöffnet, oder es werden alte Ergebnisse darin angezeigt.  
  
 Erklärung  
 Sie können die Komponententests mit einer benutzerdefinierten Datei ".runsettings" ausführen, um Codeabdeckungsoptionen zu konfigurieren. Mithilfe der Optionen können Sie Dateien einschließen oder ausschließen. Weitere Informationen finden Sie unter [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).  
  
 Auflösung  
 Es gibt zwei mögliche Fehlertypen:  
  
-   **XML-Fehler**  
  
     Öffnen Sie die Datei ".runsettings" im XML-Editor von Visual Studio. Suchen Sie nach Fehlerhinweisen.  
  
-   **Fehler in regulärem Ausdruck**  
  
     Jede Zeichenfolge in der Datei ist ein regulärer Ausdruck. Überprüfen Sie jede auf Fehler, und suchen Sie insbesondere nach Folgendem:  
  
    -   Nicht übereinstimmende Klammern (...) oder Klammern ohne Escapezeichen \\(...\\). Wenn eine Klammer in der Suchzeichenfolge übereinstimmen soll, müssen Sie diese mit einem Escapezeichen versehen. Verwenden Sie beispielsweise zum Abgleichen einer Funktion: `.*MyFunction\(double\)`  
  
    -   Sternchen oder Pluszeichen am Anfang eines Ausdrucks. Verwenden Sie einen Punkt gefolgt von einem Sternchen, damit jede Zeichenfolge übereinstimmt: `.*`  
  
### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Benutzerdefinierte Datei ".runsettings" mit falschen Ausschlüssen  
 Analyse  
 Wenn Sie eine benutzerdefinierte Datei ".runsettings" verwenden, stellen Sie sicher, dass sie Ihre Assembly enthält.  
  
 Erklärung  
 Sie können die Komponententests mit einer benutzerdefinierten Datei ".runsettings" ausführen, um Codeabdeckungsoptionen zu konfigurieren. Mithilfe der Optionen können Sie Dateien einschließen oder ausschließen. Weitere Informationen finden Sie unter [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).  
  
 Auflösung  
 Entfernen Sie alle `Include`-Knoten aus der Datei ".runsettings", und entfernen Sie dann alle `Exclude`-Knoten. Wenn das Problem damit behoben ist, fügen Sie sie schrittweise wieder hinzu.  
  
 Stellen Sie sicher, dass im „DataCollectors“-Knoten die Code Coverage angegeben wird. Vergleichen Sie ihn mit dem Beispiel in [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).  
  
## <a name="some-code-is-always-shown-as-not-covered"></a>Einiger Code wird stets als nicht abgedeckt angezeigt  
  
### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Initialisierungscode in systemeigenen DLLs wird vor der Instrumentation ausgeführt  
 Analyse  
 In statisch verknüpftem nativen Code wird ein Teil der Initialisierungsfunktion **DllMain** und Code, den sie aufruft, manchmal als nicht abgedeckt angezeigt, obwohl der Code ausgeführt wurde.  
  
 Erklärung  
 Das Code Coverage-Tool fügt kurz vor dem Start der Anwendung Instrumentation in eine Assembly ein. In jeder vor diesem Zeitpunkt geladenen Assembly wird der Initialisierungscode in **DllMain** ausgeführt, sobald die Assembly geladen wird und vor dem Ausführen der Anwendung. Dieser Code wird als nicht abgedeckt angezeigt.  
  
 Normalerweise gilt dies für statisch geladene Assemblys.  
  
 Auflösung  
 Keine  
  
## <a name="see-also"></a>Siehe auch  
 [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)

