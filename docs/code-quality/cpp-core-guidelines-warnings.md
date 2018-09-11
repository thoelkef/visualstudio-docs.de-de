---
title: C++ Core Guidelines-Warnungen
ms.date: 08/10/2017
ms.topic: conceptual
ms.assetid: 7c83814a-f21d-4323-ad5f-13bac40d3e38
author: mblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- cplusplus
ms.openlocfilehash: 035f1fe305576eb7f5bf05fb6cc5f6343e256dca
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279749"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Verwenden den C++ Core Guidelines-Überprüfungen
Der C++ Core Guidelines sind eine portable Gruppe von Richtlinien, Regeln und bewährten Methoden zum Schreiben von Code in C++, die von Experten für C++ und Designern erstellt. Visual Studio unterstützt eine Teilmenge dieser Regeln im Rahmen der Codeanalysetools derzeit für C++. Die Richtlinie kernrichtlinien werden standardmäßig in Visual Studio 2017 installiert und sind [als NuGet-Paket für Visual Studio 2015 verfügbar](#vs2015_corecheck).

## <a name="the-c-core-guidelines-project"></a>Projizieren den C++ Core Guidelines
 Bjarne Stroustrup und andere erstellt haben, werden den C++ Core Guidelines eine Anleitung zur Verwendung von modernem C++ problemlos und effektiv. Die Richtlinien Betonen Sie statische typsicherheit und Sicherheit der Ressource. Sie identifizieren Möglichkeiten zum beseitigen oder minimieren die am häufigsten fehleranfälligen Teile der Sprache, und es empfiehlt sich, wie Sie Ihren Code vereinfachen und bieten eine bessere Leistung auf zuverlässige Weise. Diese Richtlinien werden von der Standard C++ Foundation verwaltet. Weitere Informationen finden Sie in der Dokumentation, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines), und der Zugriff auf die Projektdateien der C++ Core Guidelines-Dokumentation auf [GitHub](https://github.com/isocpp/CppCoreGuidelines).

## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Aktivieren Sie die C++ Core Check-Richtlinien in der Codeanalyse
 Sie können die Codeanalyse auf Ihr Projekt aktivieren, indem Sie auswählen der **Codeanalyse für Build aktivieren** Kontrollkästchen in der **Codeanalyse** Teil der **Eigenschaftenseiten** Dialogfeld für Ihr Projekt.

 ![Eigenschaftenseite für Code Analysis Allgemeine Einstellungen](../code-quality/media/cppcorecheck_codeanalysis_general.png)

 Die C++ Core Check Regeln sind Erweiterungen für die Standard-Regelsätze, die ausgeführt werden, wenn die Codeanalyse aktiviert ist. Da die C++ Core Check-Regeln in der Entwicklungsphase befinden, einige Regeln sind gut etablierte und einige möglicherweise nicht zur Verwendung in allen bereit, aber möglicherweise noch informativ. Die Regeln in zwei Gruppen unterteilt sind: freigegeben und experimentelle. Sie können auswählen, ob die freigegebenen oder experimentellen Regeln in den Eigenschaften für Ihr Projekt auszuführen.

 ![Eigenschaftenseite "Code Analysis Extensions-Einstellungen](../code-quality/media/cppcorecheck_codeanalysis_extensions.png)

 Öffnen Sie zum Aktivieren oder deaktivieren den C++ Core Check Regelsätze, die **Eigenschaftenseiten** -Dialogfeld für Ihr Projekt. Klicken Sie unter **Konfigurationseigenschaften**, erweitern Sie **Codeanalyse**, **Erweiterungen**. Steuern Sie in der Dropdownliste neben **aktivieren C++ Core Check (freigegeben)** oder **aktivieren C++ Core Check (experimentell)**, wählen Sie **Ja** oder **keine**. Wählen Sie **OK** oder **übernehmen** zum Speichern der Änderungen.

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

-   C26494 ist Regel Type.5: immer ein Objekt zu initialisieren.

-   C26485 ist Regel Bounds.3: kein Verfall von Array in einen Zeiger.

-   C26481 ist Regel Bounds.1: Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen `span`.

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
Die C++-Core-Richtlinien aus neue Regeln hinzugefügt werden, kann die Anzahl der Warnungen, die für die bereits vorhandenen Code erstellt werden erhöhen. Sie können die vordefinierten Regelsätzen verwenden, um welche Arten von Regeln zu filtern. Ab Visual Studio 2017 Version 15.3 die sind die unterstützten Regelsätze aus:
  - **Regeln für besitzerzeiger** erzwingen [Resource-Manager überprüft, ob im Zusammenhang mit der Besitzer<T> aus den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Const-Regeln** erzwingen [Const-bezogene Überprüfungen aus den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Regeln für unformatierte Zeiger** erzwingen [Resource-Manager überprüft für unformatierte Zeiger für den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Regeln für eindeutige Zeiger** erzwingen [Resource-Manager überprüft in Bezug auf Typen mit eindeutiger zeigersemantik aus den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **– Begrenzungsregeln** erzwingen die [umschließt Profil für den C++ Core Guidelines](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Geben Sie Regeln** erzwingen die [Geben Sie den C++ Core Guidelines Profil](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).


 Sie können auch Warnungen an, die nur von einem oder mehreren Gruppen zu beschränken. Die **Native mindestens** und **empfohlen, systemeigenen** Regel umfassen C++ Core Check Regeln zusätzlich zu anderen PREfast Überprüfungen. Wählen Sie zum Anzeigen der verfügbaren-Regelsätze, öffnen Sie das Dialogfeld "Projekteigenschaften" **Code Analysis\General**, öffnen Sie die Dropdownliste in der **Rule Sets** im Kombinationsfeld, und wählen Sie **mehrere Regelsätze auswählen** . Weitere Informationen zum Verwenden von Regelsätzen in Visual Studio finden Sie unter [Regelsätze verwenden, um die Codeanalyseregeln](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makros
 Der C++ Core Richtlinien Checker umfasst eine Headerdatei die Makros definiert, die unterdrückt werden Kategorien von Warnungen im Code zu vereinfachen:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Diese Makros die Regelsätze entsprechen, und erweitern Sie in eine durch Leerzeichen getrennte Listen mit Warnzahlen. Mithilfe der entsprechenden Pragma-Konstrukte können Sie den effektiven Satz von Regeln handelt es sich für ein Projekt oder einen Codeabschnitt konfigurieren. Im folgenden Beispiel wird die Codeanalyse nur warnen, fehlende Konstanten Modifizierer:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attribute
 Microsoft Visual C++-Compiler verfügt über eine eingeschränkte Unterstützung für GSL Attribut zu unterdrücken.
Es kann so unterdrücken Sie Warnungen für Ausdrücke und Block-Anweisungen innerhalb einer Funktion verwendet werden.

```cpp
// Supress only warnings from the 'r.11' rule in expression.
[[gsl::suppress(r.11)]] new int;

// Supress all warnings from the 'r' rule group (resource management) in block.
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

 1) Mit der rechten Maustaste in der Datei im **Projektmappen-Explorer**

 2) Wählen Sie **Eigenschaften | C / C ++ | Über die Befehlszeile**

 3) In der **zusätzliche Optionen** Fenster hinzufügen `/wd26400`.

 Sie können die Befehlszeilenoption folgender Option vorübergehend deaktivieren, Codeanalyse für eine Datei durch Angabe `/analyze-`. Dadurch wird die Warnung generiert *D9025 überschreiben "/ analyze" mit "/ analyze-'*, die erinnert Sie so die Codeanalyse später wieder aktivieren.

 ## <a name="corecheck_per_file"></a> Aktivieren den C++ Core Richtlinien Checker auf bestimmten Projektdateien.
Manchmal kann es hilfreich, konzentriert sich Code analysieren und weiterhin nutzen, die Visual Studio-IDE sein. Im folgenden finden Sie ein Beispielszenario, die für große Projekte zum Zeitpunkt der Erstellung zu speichern und zu vereinfachen, Filterergebnisse verwendet werden kann.
1.  Legen Sie in der Befehlsshell die `esp.extension` und `esp.annotationbuildlevel` Umgebungsvariablen.
2.  Starten Sie Visual Studio, von der Befehlsshell, erben diese Variablen aus.
3.  Laden Sie Ihr Projekt, und öffnen Sie deren Eigenschaften.
4.  Aktivieren Sie Codeanalyse, wählen Sie die entsprechenden Regelsätze, aber aktivieren Sie Code Analysis Extensions nicht.
5.  Wechseln Sie zu der Datei, die Sie verwenden möchten, Analysieren mit der C++-Core-Richtlinien aus, und öffnen Sie deren Eigenschaften.
6.  Wählen Sie **C / C ++ \Command Befehlszeilenoptionen** und hinzufügen `/analyze:plugin EspXEngine.dll`
7.  Deaktivieren Sie die Verwendung des vorkompilierten Headers (**C / C ++ \Precompiled Header**). Dies ist erforderlich, da die Extensions-Engine versuchen kann, interne Informationen aus dem vorkompilierten Header zu lesen und, wenn die zweite mit Standardoptionen für Projekt kompiliert wurde, wird nicht kompatibel.
8.  Erstellen Sie das Projekt neu. Die allgemeine PREFast Überprüfungen sollten für alle Dateien ausführen. Da die C++-Core-Richtlinien aus, die standardmäßig nicht aktiviert ist, sollten sie nur auf die Datei ausführen, die Verwendung konfiguriert ist.

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

Sie können den C++ Core Checker nur für bestimmte Dateien ausführen, indem Sie die gleiche Weise wie [weiter oben beschriebenen](#coreckeck_per_file), aber mithilfe von MSBuild-Dateien. Die Umgebungsvariablen festgelegt werden können, mit der `BuildMacro` Element:

```xml
<ItemGroup>
    <BuildMacro Include="Esp_AnnotationBuildLevel">
      <EnvironmentVariable>true</EnvironmentVariable>
      <Value>Ignore</Value>
    </BuildMacro>
    <BuildMacro Include="Esp_Extensions">
      <EnvironmentVariable>true</EnvironmentVariable>
      <ValueCppCoreCheck.dll</Value>
    </BuildMacro>
</ItemGroup>
```

Wenn Sie nicht die Projektdatei ändern möchten, können Sie Eigenschaften in der Befehlszeile übergeben:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Nicht-MSBuild-Projekte
Wenn Sie über ein Buildsystem verwenden, die auf MSBuild basieren nicht können Sie weiterhin die voraussetzungsprüfung ausführen, aber Sie müssen (die nicht unbedingt in Zukunft unterstützt werden) mit einigen Interna der Code-Analyse-Engine-Konfiguration vertraut zu machen.

Sie müssen einige Umgebungsvariablen festlegen und den entsprechenden Befehlszeilenoptionen für den Compiler zu verwenden. Es empfiehlt sich unter der "Native Tools-Eingabeaufforderung"-Umgebung arbeiten, damit Sie nicht zum Suchen nach bestimmten Pfaden für den Compiler, zu Verzeichnissen usw. umfassen.

1.  **Umgebungsvariablen**
  - `set esp.extensions=cppcorecheck.dll` Dadurch wird die Engine an den C++ Core Guidelines-Modul zu laden.
  - `set esp.annotationbuildlevel=ignore` Dadurch wird die Logik der SAL-Anmerkungen verarbeitet werden, deaktiviert. Anmerkungen wirken sich nicht auf Code-Analyse in die C++-Core-Richtlinien aus, aber die Verarbeitung nimmt Zeit (manchmal viel Zeit). Diese Einstellung ist optional, jedoch dringend empfohlen.
  - `set caexcludepath=%include%` Es wird dringend empfohlen, dass Sie Warnungen deaktivieren, die für die Standardheader ausgelöst werden. Sie können mehrere Pfade sehen, z. B. den Pfad zu die allgemeinen Header in Ihrem Projekt hinzufügen.
2.  **Befehlszeilenoptionen**
  - `/analyze`  Aktiviert die Codeanalyse (Beachten Sie auch mit / analyze: nur und / analyze: quiet).
  - `/analyze:plugin EspXEngine.dll` Diese Option lädt die Code Analysis Extensions-Engine, in dem PREfast. Dieses Modul, lädt wiederum die C++-Core-Richtlinien aus.



## <a name="use-the-guideline-support-library"></a>Verwenden Sie die Richtlinie-Unterstützungsbibliothek
 Die Richtlinie-Unterstützungsbibliothek wurde entwickelt, können Sie die Core-Richtlinien zu befolgen. GSL enthält die Definitionen, mit denen Sie die Fehler verursachenden Konstrukte mit sicherer Alternativen zu ersetzen. Sie können z. B. Ersetzen einer `T*, length` -Paar von Parametern mit dem `span<T>` Typ. GSL finden Sie unter [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Die Bibliothek ist open Source, so können Sie die Datenquellen anzuzeigen, Kommentare und beitragen. Das Projekt finden Sie unter [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a> Verwenden Sie die C++ Core Check-Richtlinien in Visual Studio 2015-Projekten
  Wenn Sie Visual Studio 2015 verwenden, werden den C++ Core Check Code Codeanalyse-Regelsätze nicht standardmäßig installiert. Sie müssen einige zusätzliche Schritte ausführen, bevor Sie den C++ Core Check Codeanalysetools in Visual Studio 2015 aktivieren können. Microsoft bietet Support für Visual Studio 2015-Projekte mithilfe eines Nuget-Pakets. Das Paket den Namen Microsoft.CppCoreCheck, und es finden Sie unter [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Dieses Paket ist erforderlich, dass Sie mindestens Visual Studio 2015 mit Update 1 installiert haben.

 Das Paket wird auch ein anderes Paket als Abhängigkeit, eine nur-Header-Guideline Support Library (GSL) installiert. GSL steht auch auf GitHub unter [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

 Aufgrund der Art und Weise, die die Codeanalyseregeln geladen werden, müssen Sie das Microsoft.CppCoreCheck NuGet-Paket in jedem C++-Projekt installieren, die Sie in Visual Studio 2015 überprüfen möchten.

#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Um das Microsoft.CppCoreCheck-Paket Ihrem Projekt in Visual Studio 2015 hinzuzufügen.

1.  In **Projektmappen-Explorer**, mit der rechten Maustaste das Kontextmenü des Projekts in der Projektmappe zu öffnen, die das Paket hinzugefügt werden soll. Wählen Sie **NuGet-Pakete verwalten** zum Öffnen der **NuGet Package Manager**.

2.  In der **NuGet Package Manager** Fenster, suchen Sie nach Microsoft.CppCoreCheck.

     ![NuGet-Paket-Manager-Fenster zeigt CppCoreCheck-Paket](../code-quality/media/cppcorecheck_nuget_window.png)

3.  Wählen Sie das Paket Microsoft.CppCoreCheck, und wählen Sie dann die **installieren** , um die Regeln zu Ihrem Projekt hinzuzufügen.

 Das NuGet-Paket Fügt eine zusätzliche MSBuild .targets-Datei zu Ihrem Projekt, das aufgerufen wird, wenn Sie die Codeanalyse auf Ihr Projekt aktivieren. Diese TARGETS-Datei hinzugefügt das Codeanalysetool in Visual Studio die C++ Core Check Regeln als eine zusätzliche Erweiterung. Wenn das Paket installiert ist, können Sie das Dialogfeld "Eigenschaftenseiten" verwenden, aktivieren oder deaktivieren die freigegebenen und experimentellen Regeln.

