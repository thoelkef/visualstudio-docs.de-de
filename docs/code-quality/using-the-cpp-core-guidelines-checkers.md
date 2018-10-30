---
title: Verwenden den C++ Core Guidelines-Überprüfungen
ms.date: 08/14/2018
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
dev_langs:
- CPP
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 6595e8990dece15e88e07a6c8eefabd3f543bbb7
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143462"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Verwenden den C++ Core Guidelines-Überprüfungen
Der C++ Core Guidelines sind eine portable Gruppe von Richtlinien, Regeln und bewährten Methoden zum Schreiben von Code in C++, die von Experten für C++ und Designern erstellt. Visual Studio unterstützt eine Teilmenge dieser Regeln im Rahmen der Codeanalysetools derzeit für C++. Die Richtlinie kernrichtlinien werden standardmäßig in Visual Studio 2017 installiert und sind [als NuGet-Paket für Visual Studio 2015 verfügbar](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Projizieren den C++ Core Guidelines
 Bjarne Stroustrup und andere erstellt haben, werden den C++ Core Guidelines eine Anleitung zur Verwendung von modernem C++ problemlos und effektiv. Die Richtlinien Betonen Sie statische typsicherheit und Sicherheit der Ressource. Sie identifizieren Möglichkeiten zum beseitigen oder minimieren die am häufigsten fehleranfälligen Teile der Sprache, und es empfiehlt sich, wie Sie Ihren Code vereinfachen und bieten eine bessere Leistung auf zuverlässige Weise. Diese Richtlinien werden von der Standard C++ Foundation verwaltet. Weitere Informationen finden Sie in der Dokumentation, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines), und der Zugriff auf die Projektdateien der C++ Core Guidelines-Dokumentation auf [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Aktivieren Sie die C++ Core Check-Richtlinien in der Codeanalyse
 Sie können die Codeanalyse auf Ihr Projekt aktivieren, indem Sie auswählen der **Codeanalyse für Build aktivieren** Kontrollkästchen in der **Codeanalyse** Teil der **Eigenschaftenseiten** Dialogfeld für Ihr Projekt.

 ![Eigenschaftenseite für Code Analysis Allgemeine Einstellungen](media/cppcorecheck_codeanalysis_general.png)

 Eine Teilmenge der C++ Core Check Regeln ist in der Microsoft Native empfohlene Regelsatz, der ausgeführt wird standardmäßig enthalten, wenn die Codeanalyse aktiviert ist. Klicken Sie auf die Dropdownliste, und wählen Sie die Regelsätze, die Sie einschließen möchten, um zusätzliche Core Check Regeln zu aktivieren:

 ![Dropdownliste für zusätzliche C++ Core Check-Regelsätze](media/cppcorecheck_codeanalysis_extensions.png)

## <a name="examples"></a>Beispiele
 Hier ist ein Beispiel für einige der Probleme, die die C++ Core Check-Regeln finden können:

```cpp
// CoreCheckExample.cpp
// Add CppCoreCheck package and enable code analysis in build for warnings.

int main()
{
    int arr[10];           // warning C26494
    int* p = arr;          // warning C26485

    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
    {
        int* q = p + 1;    // warning C26481 (suppressed)
        p = q++;           // warning C26481 (suppressed)
    }

    return 0;
}
```

Dieses Beispiel zeigt ein Paar der Warnungen, die die C++ Core Check-Regeln finden können:

- C26494 ist Regel Type.5: immer ein Objekt zu initialisieren.

- C26485 ist Regel Bounds.3: kein Verfall von Array in einen Zeiger.

- C26481 ist Regel Bounds.1: Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen `span`.

Wenn die C++ Core Check Code Analysis Rulesets sind installiert und aktiviert, wenn Sie diesen Code kompilieren, die ersten beiden Warnungen werden ausgegeben, aber die dritte unterdrückt wird. Hier ist die Buildausgabe aus dem Beispielcode:

```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------
1>  CoreCheckExample.cpp
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Der C++ Core Guidelines gibt es lassen sich besser und sicherer Code zu schreiben. Wenn Sie eine Instanz verfügen, in denen eine Regel oder ein Profil nicht angewendet werden sollte, ist es jedoch einfach direkt im Code unterdrückt werden sollen. Sie können die `gsl::suppress` Attribut C++ Core Check verhindern, erkennen und die berichterstellung einer Verletzung einer Regel in den folgenden Codeblock. Sie können einzelne Anweisungen aus, um bestimmte Regeln unterdrücken kennzeichnen. Können Sie auch das gesamte begrenzungsprofil unterdrücken, durch das Schreiben von `[[gsl::suppress(bounds)]]` ohne eine spezielle regelzahl.

## <a name="supported-rule-sets"></a>Unterstützt von Regelsätzen
Die C++-Core-Richtlinien aus neue Regeln hinzugefügt werden, kann die Anzahl der Warnungen, die für die bereits vorhandenen Code erstellt werden erhöhen. Sie können die vordefinierten Regelsätzen verwenden, um welche Arten von Regeln zu filtern.
Referenzthemen für die meisten Regeln unterliegen [Visual Studio C++ Core überprüfen Reference](code-analysis-for-cpp-corecheck.md).

Ab Visual Studio 2017 Version 15.3 die sind die unterstützten Regelsätze aus:
- **Regeln für besitzerzeiger** erzwingen [Resource-Manager überprüft, ob im Zusammenhang mit der Besitzer<T> aus den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Const-Regeln** erzwingen [Const-bezogene Überprüfungen aus den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

- **Regeln für unformatierte Zeiger** erzwingen [Resource-Manager überprüft für unformatierte Zeiger für den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **Regeln für eindeutige Zeiger** erzwingen [Resource-Manager überprüft in Bezug auf Typen mit eindeutiger zeigersemantik aus den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

- **– Begrenzungsregeln** erzwingen die [umschließt Profil für den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

- **Geben Sie Regeln** erzwingen die [Geben Sie den C++ Core Guidelines Profil](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

**Visual Studio 2017 Version 15.5**:

- **Klasse von Regeln** einige Regeln, die auf die richtige Verwendung von speziellen Memberfunktionen und virtuellen Spezifikationen zu konzentrieren. Dies ist eine Teilmenge der Überprüfungen, empfohlen für [Klassen und Klassenhierarchien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class).
- **– Parallelitätsregeln** eine einzige Regel, die Guard deklarierten Objekte abfängt. Weitere Informationen finden Sie unter [Richtlinien im Zusammenhang mit Parallelität](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency).
- **Deklarationsregeln** eine Reihe von Regeln aus der [Schnittstellen Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) der Schwerpunkt liegt auf der Funktionsweise der globalen Variablen deklariert werden.
- **Funktionieren Regeln** zwei Überprüfungen, die mit der Annahme der unterstützen die `noexcept` Spezifizierer. Dies ist ein Teil der Richtlinien für die [Deaktivieren der Funktion Entwurf und Implementierung](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions).
- **Regeln für gemeinsame Zeiger** als Teil der [ressourcenverwaltung](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) Erzwingung von Richtlinien, wir hinzugefügt, einige Regeln, die spezifisch für die Verwendung von freigegebenen Zeiger an Funktionen übergeben oder die lokal verwendet werden.
- **Formatierungsregeln** eine einfache, aber wichtigen Prüfung, die Verwendung von gesperrt [Goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Dies ist der erste Schritt bei der Verbesserung der Programmierung von Stil und die Verwendung von Ausdrücken und Anweisungen in C++.

**Visual Studio 2017-Version 15.6:**

- **Arithmetischer Regeln** Regeln zur Erkennung arithmetischer [Überlauf](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-overflow), [Operations signierter](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-unsigned) und [bit Manipulation](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-nonnegative).

Sie können auch Warnungen an, die nur von einem oder mehreren Gruppen zu beschränken. Die **Native mindestens** und **empfohlen, systemeigenen** Regel umfassen C++ Core Check Regeln zusätzlich zu anderen PREfast Überprüfungen. Wählen Sie zum Anzeigen der verfügbaren-Regelsätze, öffnen Sie das Dialogfeld "Projekteigenschaften" **Code Analysis\General**, öffnen Sie die Dropdownliste in der **Rule Sets** im Kombinationsfeld, und wählen Sie **mehrere Regelsätze auswählen** . Weitere Informationen zum Verwenden von Regelsätzen in Visual Studio finden Sie unter [Regelsätze verwenden, um die Codeanalyseregeln](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makros

Der C++ Core Richtlinien Checker umfasst eine Headerdatei, die Makros definiert, die unterdrückt werden Kategorien von Warnungen im Code zu vereinfachen:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Diese Makros die Regelsätze entsprechen, und erweitern Sie in eine durch Leerzeichen getrennte Liste mit Warnzahlen. Verwenden Sie die entsprechenden Pragma-Konstrukte, können Sie den effektiven Satz von Regeln, die für ein Projekt sind oder einen Codeabschnitt konfigurieren. Im folgenden Beispiel warnt Codeanalyse nur Konstanten Modifizierer fehlt:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attribute

Microsoft Visual C++-Compiler verfügt über eine eingeschränkte Unterstützung für GSL Attribut zu unterdrücken. Es kann so unterdrücken Sie Warnungen für Ausdrücke und Block-Anweisungen innerhalb einer Funktion verwendet werden.

```cpp
// Suppress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Suppress all warnings from the 'r' rule group (resource management) in block.
[[gsl::suppress(r)]]
{
    new int;
}

// Suppress only one specific warning number.
// For declarations, you may need to use the surrounding block.
// Macros are not expanded inside of attributes.
// Use plain numbers instead of macros from the warnings.h.
[[gsl::suppress(26400)]]
{
    int *p = new int;
}
```

## <a name="suppressing-analysis-by-using-command-line-options"></a>Unterdrücken der Analyse mithilfe von Befehlszeilenoptionen

Anstelle von #pragmas können Befehlszeilenoptionen in der Datei-Eigenschaftenseite Sie so unterdrücken Sie Warnungen für ein Projekt oder eine einzelne Datei. Um beispielsweise die Warnung deaktivieren 26400 für eine Datei:

1. Mit der rechten Maustaste in der Datei im **Projektmappen-Explorer**

2. Wählen Sie **Eigenschaften | C / C ++ | Über die Befehlszeile**

3. In der **zusätzliche Optionen** Fenster hinzufügen `/wd26400`.

Sie können die Befehlszeilenoption vorübergehend deaktivieren, Codeanalyse für eine Datei durch Angabe `/analyze-`. Dadurch wird die Warnung *D9025 Überschreiben '/ analyze-mit "/ analyze-'*, die erinnert Sie daran, Codeanalyse später wieder aktivieren.

## <a name="corecheck_per_file"></a> Aktivieren den C++ Core Richtlinien Checker auf bestimmten Projektdateien.

Manchmal kann es hilfreich, konzentriert sich Code analysieren und immer noch mit Visual Studio-IDE sein. Das folgende Beispielszenario kann zum Zeitpunkt der Erstellung zu speichern und zu vereinfachen, Filterergebnisse für große Projekte verwendet werden:

1. Legen Sie in der Befehlsshell die `esp.extension` und `esp.annotationbuildlevel` Umgebungsvariablen.
2. Um diese Variablen zu erben, starten Sie Visual Studio von der Befehlsshell aus.
3. Laden Sie Ihr Projekt, und öffnen Sie deren Eigenschaften.
4. Aktivieren Sie Codeanalyse, wählen Sie die entsprechenden Regelsätze, aber aktivieren Sie Code Analysis Extensions nicht.
5. Wechseln Sie zu der Datei, die Sie verwenden möchten, Analysieren mit der C++-Core-Richtlinien aus, und öffnen Sie deren Eigenschaften.
6. Wählen Sie **C / C ++ \Command Befehlszeilenoptionen** und hinzufügen `/analyze:plugin EspXEngine.dll`
7. Deaktivieren Sie die Verwendung des vorkompilierten Headers (**C / C ++ \Precompiled Header**). Dies ist erforderlich, da die Engine Erweiterungen versuchen möglicherweise, zum Lesen von internen Informationen aus der vorkompilierten Headerdateien (PCH); Wenn die PCH mit Standardoptionen für Projekt kompiliert wird, wird er nicht kompatibel.
8. Erstellen Sie das Projekt neu. Die allgemeine PREFast Überprüfungen sollten für alle Dateien ausführen. Da die C++-Core-Richtlinien aus, die standardmäßig nicht aktiviert ist, sollten sie nur auf die Datei ausführen, die für dessen Verwendung konfiguriert ist.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Gewusst wie: Verwenden Sie den C++ Core Richtlinien Checker außerhalb von Visual Studio

Sie können die C++ Core Guidelines-Überprüfungen in automatisierten Builds verwenden.

### <a name="msbuild"></a>MSBuild
 MSBuild-Umgebung durch benutzerdefinierte Targets-Dateien ist die Analyse von systemeigenem Code Checker (PREfast) integriert. Sie können Projekteigenschaften verwenden, um ihn zu aktivieren und fügen Sie die Richtlinien aus der C++ Core (dem PREfast basiert) hinzu:

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```

Stellen Sie sicher, dass Sie diese Eigenschaften vor dem Importieren der Datei Microsoft.Cpp.targets hinzufügen. Sie können bestimmte Regelsätze auswählen oder Erstellen eines benutzerdefinierten Regelsatzes oder verwenden Sie den Standardregelsatz, der andere PREfast Prüfungen enthält.

Sie können den C++ Core Checker nur für bestimmte Dateien ausführen, indem Sie die gleiche Weise wie [weiter oben beschriebenen](#corecheck_per_file), aber mithilfe von MSBuild-Dateien. Die Umgebungsvariablen festgelegt werden können, mit der `BuildMacro` Element:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>CppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Wenn Sie nicht die Projektdatei ändern möchten, können Sie Eigenschaften in der Befehlszeile übergeben:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Nicht-MSBuild-Projekte

Wenn Sie über ein Buildsystem verwenden, die auf MSBuild basieren nicht können Sie weiterhin die voraussetzungsprüfung ausführen, aber Sie müssen mit einigen Interna der Code-Analyse-Engine-Konfiguration vertraut zu machen. Diese internen Werte werden nicht unbedingt in Zukunft unterstützt werden.

Sie müssen einige Umgebungsvariablen festlegen und verwenden Sie die entsprechende Befehlszeilenoptionen für den Compiler. Es empfiehlt sich unter der "Native Tools-Eingabeaufforderung"-Umgebung arbeiten, damit Sie nicht zum Suchen nach bestimmten Pfaden für den Compiler, zu Verzeichnissen usw. umfassen.

1. **Umgebungsvariablen**
   - `set esp.extensions=cppcorecheck.dll` Dadurch wird die Engine an den C++ Core Guidelines-Modul zu laden.
   - `set esp.annotationbuildlevel=ignore` Dadurch wird die Logik, die SAL-Anmerkungen verarbeitet deaktiviert. Anmerkungen wirken sich nicht auf Code-Analyse in die C++-Core-Richtlinien aus, aber deren Verarbeitung dauert (manchmal eine lange Zeit). Diese Einstellung ist optional, jedoch dringend empfohlen.
   - `set caexcludepath=%include%` Es wird dringend empfohlen, dass Sie Warnungen deaktivieren, die für die Standardheader ausgelöst werden. Sie können mehrere Pfade sehen, z. B. den Pfad zu die allgemeinen Header in Ihrem Projekt hinzufügen.
2. **Befehlszeilenoptionen**
   - `/analyze`  Aktiviert die Codeanalyse (Beachten Sie auch mit / analyze: nur und / analyze: quiet).
   - `/analyze:plugin EspXEngine.dll` Diese Option lädt die Code Analysis Extensions-Engine, in dem PREfast. Dieses Modul, lädt wiederum die C++-Core-Richtlinien aus.

## <a name="use-the-guideline-support-library"></a>Verwenden Sie die Richtlinie-Unterstützungsbibliothek
 Die Richtlinie-Unterstützungsbibliothek wurde entwickelt, können Sie die Core-Richtlinien zu befolgen. GSL enthält die Definitionen, mit denen Sie die Fehler verursachenden Konstrukte mit sicherer Alternativen zu ersetzen. Sie können z. B. Ersetzen einer `T*, length` -Paar von Parametern mit dem `span<T>` Typ. GSL finden Sie unter [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Die Bibliothek ist Open Source-, damit Sie die Datenquellen anzuzeigen, Kommentare oder beitragen können. Das Projekt finden Sie unter [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

## <a name="vs2015_corecheck"></a> Verwenden Sie die C++ Core Check-Richtlinien in Visual Studio 2015-Projekten

Wenn Sie Visual Studio 2015 verwenden, werden den C++ Core Check Code Codeanalyse-Regelsätze nicht standardmäßig installiert. Sie müssen einige zusätzliche Schritte ausführen, bevor Sie den C++ Core Check Codeanalysetools in Visual Studio 2015 aktivieren können. Microsoft bietet Support für Visual Studio 2015-Projekte mithilfe eines Nuget-Pakets. Das Paket den Namen Microsoft.CppCoreCheck, und es finden Sie unter [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Dieses Paket ist erforderlich, dass Sie mindestens Visual Studio 2015 mit Update 1 installiert haben.

Das Paket wird auch ein anderes Paket als Abhängigkeit, eine nur-Header-Guideline Support Library (GSL) installiert. GSL steht auch auf GitHub unter [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

Aufgrund der Art und Weise, die die Codeanalyseregeln geladen werden, müssen Sie das Microsoft.CppCoreCheck NuGet-Paket in jedem C++-Projekt installieren, die Sie in Visual Studio 2015 überprüfen möchten.

### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Um das Microsoft.CppCoreCheck-Paket Ihrem Projekt in Visual Studio 2015 hinzuzufügen.

1. In **Projektmappen-Explorer**, mit der rechten Maustaste das Kontextmenü des Projekts in der Projektmappe zu öffnen, die das Paket hinzugefügt werden soll. Wählen Sie **NuGet-Pakete verwalten** zum Öffnen der **NuGet Package Manager**.

2. In der **NuGet Package Manager** Fenster, suchen Sie nach Microsoft.CppCoreCheck.

    ![NuGet-Paket-Manager-Fenster zeigt CppCoreCheck-Paket](../code-quality/media/cppcorecheck_nuget_window.png)

3. Wählen Sie das Paket Microsoft.CppCoreCheck, und wählen Sie dann die **installieren** , um die Regeln zu Ihrem Projekt hinzuzufügen.

   Das NuGet-Paket Fügt eine zusätzliche MSBuild *targets* Datei zum Projekt, das aufgerufen wird, wenn Sie die Codeanalyse auf Ihr Projekt aktivieren. Dies *targets* Datei fügt die C++ Core Check Regeln als eine zusätzliche Erweiterung an, um das Codeanalysetool in Visual Studio. Wenn das Paket installiert ist, können Sie das Dialogfeld "Eigenschaftenseiten" verwenden, aktivieren oder deaktivieren die freigegebenen und experimentellen Regeln.

## <a name="see-also"></a>Siehe auch

- [Referenz zu Visual Studio C++ Core Check](code-analysis-for-cpp-corecheck.md)