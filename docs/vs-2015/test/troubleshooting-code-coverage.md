---
title: Problembehandlung bei der Code Coverage | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: 13
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bf21286143b2b9543c834f00ed31ddaa4cef63
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660376"
---
# <a name="troubleshooting-code-coverage"></a>Problembehandlung bei der Code Coverage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Tool zur Code Coverage-Analyse in Visual Studio werden Daten für native und verwaltete Assemblys (DLL- oder EXE-Dateien) erfasst. In einigen Fällen wird im Fenster "Code Coverage-Ergebnisse" jedoch ein Fehler ähnlich dem "leere Ergebnisse generiert:..." angezeigt. Es gibt mehrere mögliche Gründe, warum dies passieren könnte. Dieses Thema soll Ihnen helfen, diese Probleme zu beheben.

## <a name="what-you-should-see"></a>Anzeige im Normalfall
 Wenn Sie Im Menü „Test“ den Befehl **Code Coverage analysieren** auswählen und der Buildvorgang sowie die Tests erfolgreich ausgeführt werden, sollte im Fenster „Code Coverage“ eine Ergebnisliste angezeigt werden. Sie müssen möglicherweise die Elemente erweitern, um die Details anzuzeigen.

 ![Code Coverage-Ergebnisse mit Färbung](../test/media/codecoverage1.png "CodeCoverage1")

 Weitere Informationen finden Sie unter [Using Code Coverage to Determine How Much Code is being Tested (Wie Sie feststellen können, wie viel Code untersucht wird)](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Mögliche Gründe dafür, dass keine oder alte Ergebnisse angezeigt werden

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Verwenden Sie die richtige Edition von Visual Studio?
 Sie benötigen Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Es wurden keine Tests ausgeführt.
 Analyse überprüfen Sie das Ausgabefenster. Wählen Sie in der Dropdownliste **Ausgabe anzeigen von** die Option **Tests** aus. Überprüfen Sie, ob Warnungen oder Fehler protokolliert wurden.

 Erläuterung der Code Coverage-Analyse wird während der Ausführung der Tests ausgeführt. Sie schließt nur Assemblys ein, die während der Tests in den Arbeitsspeicher geladen werden. Wenn kein Test ausgeführt wird, gibt es nichts zur Codeabdeckung zu berichten.

 Lösung wählen Sie im Test-Explorer **alle ausführen** aus, um zu überprüfen, ob die Tests erfolgreich ausgeführt wurden. Beheben Sie alle Fehler, bevor Sie **Code Coverage analysieren** verwenden.

### <a name="youre-looking-at-a-previous-result"></a>Sie sehen sich ein vorheriges Ergebnis an.
 Wenn Sie die Tests ändern und erneut ausführen, können das vorherige Codeabdeckungsergebnis und die Codefarbe der alten Ausführung noch sichtbar sein.

1. Führen Sie "Codeabdeckung analysieren" aus.

2. Überprüfen Sie, ob Sie das aktuelle Resultset im Fenster "Codeabdeckungsergebnisse" ausgewählt haben.

### <a name="pdb-symbol-files-are-unavailable"></a>PDB-Dateien (Symboldateien) sind nicht verfügbar
 Analyse öffnen Sie den Kompilierungs Zielordner (normalerweise "bin\debug"), und überprüfen Sie, ob für jede Assembly eine PDB-Datei im gleichen Verzeichnis wie die dll-oder exe-Datei vorhanden ist.

 Erläuterung die Code Coverage-Engine erfordert, dass jede Assembly während des Testlaufs auf die zugeordnete PDB-Datei zugreifen kann. Wenn für eine bestimmte Assembly keine PDB-Datei zur Verfügung steht, wird sie nicht analysiert.

 Die PDB-Datei und die DLL- oder EXE-Datei müssen im selben Buildvorgang generiert werden.

 Lösung stellen Sie sicher, dass die Buildeinstellungen die PDB-Datei generieren. Wenn die PDB-Dateien beim Erstellen des Projekts nicht aktualisiert werden, öffnen Sie die Projekteigenschaften, wählen Sie die Seite **Build** aus, wählen Sie **Erweitert** aus, und überprüfen Sie **Debuginformationen**.

 Wenn sich die PDB-Datei und die DLL- oder EXE-Datei an verschiedenen Speicherorten befinden, kopieren Sie die PDB-Datei in dasselbe Verzeichnis. Es ist auch möglich, die Code Coverage-Engine so zu konfigurieren, dass an anderen Speicherorten nach PDB-Dateien gesucht wird. Weitere Informationen finden Sie unter [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>Verwenden einer instrumentierten oder optimierten Binärdatei
 Die Analyse bestimmt, ob die Binärdatei einer erweiterten Optimierung unterzogen wurde, beispielsweise bei der Profil gesteuerten Optimierung, oder wurde durch ein Profil Erstellungs Tool wie "VSInstr. exe" oder "VSPerfMon. exe" instrumentiert.

 Erläuterung wenn eine Assembly bereits durch ein anderes Profil Erstellungs Tool instrumentiert oder optimiert wurde, wird die Assembly aus der Code Coverage Analyse weggelassen.

 Die Codeabdeckungsanalyse kann für solche Assemblys nicht ausgeführt werden.

 Lösung: Deaktivieren Sie die Optimierung, und verwenden Sie einen neuen Build.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Code ist kein verwalteter (.NET) oder systemeigener Code (C++)
 Analyse überprüfen Sie, ob Sie einige Tests für verwalteten C++ Code oder Code ausführen.

 Die Erläuterung der Code Coverage-Analyse in Visual Studio ist nur für verwalteten undC++nativen () Code verfügbar. Wenn Sie mit Tools von Drittanbietern arbeiten, wird ein Teil des Codes oder der gesamte Code möglicherweise auf einer anderen Plattform ausgeführt.

 Auflösung ist nicht verfügbar.

### <a name="assembly-has-been-installed-by-ngen"></a>Assembly wurde durch NGen installiert
 Analyse überprüfen Sie, ob die Assembly nicht aus dem Cache für systemeigene Images geladen wurde.

 Erläuterung aus Leistungsgründen werden Assemblys von systemeigenen Images nicht analysiert. Weitere Informationen finden Sie unter [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/library/44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66).

 Auflösung verwenden Sie eine MSIL-Version der Assembly. Verarbeiten Sie sie nicht mit NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Benutzerdefinierte Datei ".runsettings" mit ungültiger Syntax
 Analyse Wenn Sie eine benutzerdefinierte Datei ". RunSettings" verwenden, kann Sie einen Syntax Fehler enthalten.

 Dies führt dazu, dass keine Codeabdeckungsanalyse ausgeführt wird. Entweder wird das Fenster "Codeabdeckung" am Ende des Testlaufs nicht geöffnet, oder es werden alte Ergebnisse darin angezeigt.

 Erläuterung Sie können die Komponententests mit einer benutzerdefinierten Datei ". RunSettings" ausführen, um Code Coverage Optionen zu konfigurieren. Mithilfe der Optionen können Sie Dateien einschließen oder ausschließen. Weitere Informationen finden Sie unter [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).

 Lösung es gibt zwei mögliche Fehlertypen:

- **XML-Fehler**

     Öffnen Sie die Datei ".runsettings" im XML-Editor von Visual Studio. Suchen Sie nach Fehlerhinweisen.

- **Fehler in regulärem Ausdruck**

  Jede Zeichenfolge in der Datei ist ein regulärer Ausdruck. Überprüfen Sie jede auf Fehler, und suchen Sie insbesondere nach Folgendem:

  - Nicht übereinstimmende Klammern (...) oder Klammern ohne Escapezeichen \\(...\\). Wenn eine Klammer in der Suchzeichenfolge übereinstimmen soll, müssen Sie diese mit einem Escapezeichen versehen. Verwenden Sie beispielsweise zum Abgleichen einer Funktion: `.*MyFunction\(double\)`

  - Sternchen oder Pluszeichen am Anfang eines Ausdrucks. Verwenden Sie einen Punkt gefolgt von einem Sternchen, damit jede Zeichenfolge übereinstimmt: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Benutzerdefinierte Datei ".runsettings" mit falschen Ausschlüssen
 Analyse Wenn Sie eine benutzerdefinierte Datei ". RunSettings" verwenden, stellen Sie sicher, dass Sie Ihre Assembly enthält.

 Erläuterung Sie können die Komponententests mit einer benutzerdefinierten Datei ". RunSettings" ausführen, um Code Coverage Optionen zu konfigurieren. Mithilfe der Optionen können Sie Dateien einschließen oder ausschließen. Weitere Informationen finden Sie unter [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).

 Auflösung entfernen Sie alle `Include` Knoten aus der Datei ". RunSettings", und entfernen Sie dann alle `Exclude` Knoten. Wenn das Problem damit behoben ist, fügen Sie sie schrittweise wieder hinzu.

 Stellen Sie sicher, dass im „DataCollectors“-Knoten die Code Coverage angegeben wird. Vergleichen Sie ihn mit dem Beispiel in [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Einiger Code wird stets als nicht abgedeckt angezeigt

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Initialisierungscode in systemeigenen DLLs wird vor der Instrumentation ausgeführt
 Analyse in statisch verknüpftem nativen Code wird ein Teil der Initialisierungsfunktion **DllMain** und der Code, den Sie aufruft, manchmal als nicht abgedeckt angezeigt, obwohl der Code ausgeführt wurde.

 Erläuterung das Code Coverage Tool funktioniert, indem Sie Instrumentation in eine Assembly einfügen, kurz bevor die Ausführung der Anwendung gestartet wird. In jeder vor diesem Zeitpunkt geladenen Assembly wird der Initialisierungscode in **DllMain** ausgeführt, sobald die Assembly geladen wird und vor dem Ausführen der Anwendung. Dieser Code wird als nicht abgedeckt angezeigt.

 Normalerweise gilt dies für statisch geladene Assemblys.

 Auflösung keine.

## <a name="see-also"></a>Siehe auch
 [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
