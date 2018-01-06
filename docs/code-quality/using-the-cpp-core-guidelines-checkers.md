---
title: Verwenden die Spielsteine C++ Core Richtlinien | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload: cplusplus
ms.openlocfilehash: cadee7d9cae0c59333a034e6f0ea12049bf3853f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-c-core-guidelines-checkers"></a>Verwenden die Spielsteine C++-Core-Richtlinien
Die C++-Core-Richtlinien sind eine portable Satz von Richtlinien, Regeln und bewährte Methoden zum Schreiben von Code in C++, die von C++-Experten und Designern erstellt. Visual Studio unterstützt derzeit eine Teilmenge dieser Regeln als Teil seiner Codeanalysetools für C++. Die zentrale Richtlinie Prüfer werden standardmäßig in Visual Studio 2017 installiert und sind [als NuGet-Paket für Visual Studio 2015 verfügbar](#vs2015_corecheck).
  
## <a name="the-c-core-guidelines-project"></a>Das C++-Core-Richtlinien-Projekt  
 Durch Bjarne Stroustrup und andere erstellt haben, werden die C++-Core-Richtlinien eine Anleitung zur Verwendung von modernen C++ problemlos und effektiv. Die Richtlinien hervorheben statische typsicherheit und Sicherheit der Ressource. Sie Identifizieren von Lösungen zum Entfernen oder minimieren, die am häufigsten fehleranfällig Teile der Sprache und wie Sie Ihren Code zu vereinfachen, und bieten eine bessere Leistung auf zuverlässige Weise vorgeschlagen. Diese Richtlinien werden von der standardmäßigen C++-Foundation verwaltet. Weitere Informationen finden Sie in der Dokumentation [C++ Core Richtlinien](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines), und der Zugriff auf die C++-Core-Richtlinien Dokumentation Projektdateien auf [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Aktivieren Sie die Richtlinien C++ Core überprüfen in der Codeanalyse  
 Kann Codeanalyse auf Ihrem Projekt durch Auswählen der **Codeanalyse für Build aktivieren** Kontrollkästchen in der **Codeanalyse** im Abschnitt der **Eigenschaftenseiten** Dialogfeld für das Projekt.  
  
 ![Eigenschaftenseite für Code Analysis-Allgemein-Einstellungen](../code-quality/media/cppcorecheck_codeanalysis_general.png "CPPCoreCheck_CodeAnalysis_General")  
  
 Die C++-Kern überprüfen Regeln sind Erweiterungen die Standardregelsätze, die ausgeführt werden, wenn die Codeanalyse aktiviert ist. Da die C++ Core überprüfen Regeln in der Entwicklungsphase befinden, einige Regeln sind etabliert und einige möglicherweise nicht zur Verwendung für den gesamten Code bereit, aber möglicherweise noch informativ. Die Regeln sind in zwei Gruppen unterteilt: freigegeben und experimentellen. Sie können auswählen, ob freigegeben oder experimentellen Regeln in den Eigenschaften für das Projekt auszuführen.  
  
 ![Eigenschaftenseite für Analysis-Codeerweiterungen Einstellungen](../code-quality/media/cppcorecheck_codeanalysis_extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
 Öffnen Sie zum Aktivieren oder deaktivieren die Regelsätze C++ Core überprüfen, die **Eigenschaftenseiten** -Dialogfeld für Ihr Projekt. Klicken Sie unter **Konfigurationseigenschaften**, erweitern Sie **Codeanalyse**, **Erweiterungen**. In der Dropdownliste neben steuern **aktivieren C++ Core überprüfen (freigegeben)** oder **aktivieren C++ Core überprüfen (experimentell)**, wählen Sie **Ja** oder **keine**. Wählen Sie **OK** oder **übernehmen** zum Speichern der Änderungen.  
  
## <a name="examples"></a>Beispiele  
 Hier ist ein Beispiel für einige der Probleme, die die Regeln C++ Core überprüfen finden können:  
  
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
  
 Dieses Beispiel zeigt nur einige der Warnungen, die die Regeln C++ Core überprüfen finden können:  
  
-   C26494 ist Regel Type.5: immer ein Objekt initialisiert werden.  
  
-   C26485 ist Regel Bounds.3: keine Decay Array in einen Zeiger.  
  
-   C26481 ist Regel Bounds.1: Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen `span`.  
  
 Wenn die C++ Core überprüfen Code Analysis-Rulesets sind installiert und aktiviert, wenn Sie diesen Code kompilieren, die ersten beiden Warnungen ausgegeben werden, aber das dritte unterdrückt wird. Hier ist die Buildausgabe aus den folgenden Code ein:  
  
```Output
1>------ Build started: Project: CoreCheckExample, Configuration: Debug Win32 ------  
1>  CoreCheckExample.cpp  
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.exe  
1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\Projects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)  
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(6): warning C26494: Variable 'arr' is uninitialized. Always initialize an object. (type.5: http://go.microsoft.com/fwlink/p/?LinkID=620421)  
c:\users\username\documents\visual studio 2015\projects\corecheckexample\corecheckexample\corecheckexample.cpp(7): warning C26485: Expression 'arr': No array to pointer decay. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)  
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
```  
  
Die C++-Core-Richtlinien bestehen lassen sich besser und sicherer Code zu schreiben. Wenn Sie eine Instanz verfügen, in denen eine Regel oder ein Profil angewendet werden sollte nicht, ist es jedoch einfach direkt im Code zu unterdrücken. Sie können die `gsl::suppress` Attribut C++ Core überprüfen verhindern, dass erkennen und eine Verletzung einer Regel in den folgenden Codeblock reporting. Sie können einzelne Anweisungen aus, um bestimmte Regeln unterdrücken kennzeichnen. Sie können auch das gesamte Grenzen Profil unterdrücken, indem das Schreiben von `[[gsl::suppress(bounds)]]` ohne eine bestimmte Regel Zahl.  

## <a name="supported-rule-sets"></a>Unterstützt von Regelsätzen
Die C++-Core-Richtlinien aus neue Regeln hinzugefügt werden, erhöhen Sie die Anzahl der Warnungen, die für bereits vorhandene Code erstellt werden. Sie können die vordefinierten Regelsätzen verwenden, um zu filtern, welche Arten von Regeln zu aktivieren. Referenzthemen für die meisten Regeln befinden sich unter [Visual Studio C++ Core überprüfen Reference](code-analysis-for-cpp-corecheck.md).

Ab Visual Studio 2017 Version 15.3 sind unterstützten Regelsätze aus: 
  - **Besitzer Zeiger Regeln** erzwingen [ressourcenverwaltung überprüft im Zusammenhang mit Besitzer<T> von den C++-Core-Richtlinien](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Const Regeln** erzwingen [Const-bezogene Überprüfungen von den C++-Core-Richtlinien](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con-constants-and-immutability).

  - **Regeln für unformatierte Zeiger** erzwingen [ressourcenverwaltung Hier wird überprüft, ob von den C++-Core-Richtlinien im Zusammenhang mit unformatierten Zeigern](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Regeln für eindeutige Zeiger** erzwingen [ressourcenverwaltung überprüft im Zusammenhang mit Typen mit eindeutigen Zeiger Semantik von den C++-Core-Richtlinien](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#r-resource-management).

  - **Umschließt Regeln** Erzwingen der [umschließt Profil gegen die C++-Core-Richtlinien](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

  - **Geben Sie Regeln** Erzwingen der [Typ Profil gegen die C++-Core-Richtlinien](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#prosafety-type-safety-profile).

  **Visual Studio 2017 Version 15.5**:
  - **-Klasse Regeln** einige Regeln, die auf die richtige Verwendung von virtuellen Spezifikationen und spezielle Methoden konzentrieren. Dies ist eine Teilmenge von Überprüfungen für empfohlen [Klassen und Klassenhierarchien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-class). 
  - **Parallelitätsregeln** eine einzelne Regel die Guard Badlyly deklariert Objekte abfängt. Weitere Informationen finden Sie unter [Richtlinien im Zusammenhang mit der Parallelität](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-concurrency). 
  - **Deklaration Regeln** eine Reihe von Regeln aus der [Schnittstellen Richtlinien](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-interfaces) welche konzentrieren wie globale Variablen deklariert werden.  
  - **Regeln-Funktion** zwei Überprüfungen, die bei der Übernahme von unterstützen die `noexcept` Spezifizierer. Dies ist ein Teil der Richtlinien für die [Deaktivieren der Funktion Entwurf und Implementierung](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-functions). 
  - **Freigegebene Zeiger Regeln** als Teil einer [ressourcenverwaltung](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#S-resource) Durchsetzung von Richtlinien, wir hinzugefügt, einige Regeln, die speziell für wie freigegebener Zeiger an Funktionen übergeben oder lokal verwendet werden.  
  - **Stilregeln** eine einfache, aber wichtige überprüfen Sie die Verwendung von gesperrt [Goto](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Res-goto). Dies ist der erste Schritt bei der Verbesserung der Stil und einem verwenden Ausdrücke und-Anweisungen in C++ codieren. 


 Sie können auswählen, um Warnungen an, die nur eine oder einige der Gruppen zu beschränken. Die **Native Minimum** und **empfohlen, systemeigenen** Regel umfassen Regeln zusätzlich zu anderen PREfast Überprüfungen C++ Core überprüfen. Wählen Sie zum Anzeigen der verfügbaren-Regelsätze, öffnen Sie das Dialogfeld Projekteigenschaften **Code Analysis\General**, öffnen Sie die Dropdownliste in der **Regelsätzen** Kombinationsfelds und Pick **wählen Sie mehrere Regelsätze** . Weitere Informationen zum Verwenden von Regelsätzen in Visual Studio finden Sie unter [mithilfe von Regelsätzen zum Gruppe Codeanalyseregeln](using-rule-sets-to-group-code-analysis-rules.md).

## <a name="macros"></a>Makros
 Die C++-Core-Richtlinien aus enthält eine Headerdatei, die Makros definiert, die gesamte Kategorien von Warnungen in Code unterdrücken erleichtern:

```cpp
ALL_CPPCORECHECK_WARNINGS
CPPCORECHECK_TYPE_WARNINGS
CPPCORECHECK_RAW_POINTER_WARNINGS
CPPCORECHECK_CONST_WARNINGS
CPPCORECHECK_OWNER_POINTER_WARNINGS
CPPCORECHECK_UNIQUE_POINTER_WARNINGS
CPPCORECHECK_BOUNDS_WARNINGS
```

Diese Makros Regelsätze entsprechen und in eine durch Leerzeichen getrennte Liste mit Warnungsnummern erweitern. Verwenden Sie die entsprechenden Pragma-Konstrukte, können Sie den effektiven Satz von Regeln, die interessante für ein Projekt ist oder einen Codeabschnitt konfigurieren. Im folgenden Beispiel wird Codeanalyse warnen nur Konstante Modifizierer fehlt:

```cpp
#include <CppCoreCheck\Warnings.h>
#pragma warning(disable: ALL_CPPCORECHECK_WARNINGS)
#pragma warning(default: CPPCORECHECK_CONST_WARNINGS)
```

## <a name="attributes"></a>Attribute
 Microsoft Visual C++-Compiler wurde eine eingeschränkte Unterstützung für GSL Attribut zu unterdrücken.
Es kann zum Unterdrücken von Warnungen für Ausdruck und Block-Anweisungen innerhalb einer Funktion verwendet werden.

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

## <a name="suppressing-analysis-by-using-command-line-options"></a>Unterdrücken der Analyse mithilfe der Befehlszeilenoptionen
 Anstelle von #pragmas können Befehlszeilenoptionen auf der Eigenschaftenseite der Datei Sie um Warnungen für ein Projekt oder eine einzelne Datei zu unterdrücken. Beispielsweise, um die Warnung deaktivieren 26400 für eine Datei:
 
 1) Mit der rechten Maustaste in der Datei im **Projektmappen-Explorer**

 2) Wählen Sie **Eigenschaften | C / C ++ | Über die Befehlszeile**

 3) In der **Zusatzoptionen** Fenster hinzufügen `/wd26400`.

 Sie können die Befehlszeilenoption alle Codeanalyse für eine Datei durch Angabe vorübergehend deaktivieren `/analyze-`. Dadurch wird die Warnung erzeugt *D9025 überschreiben "/ analyze" mit "/ analyze-"*, die daran erinnert Sie Codeanalyse später erneut aktivieren.

 ## <a name="corecheck_per_file"></a>Aktivieren das C++ Core Richtlinien Checker auf bestimmte Projektdateien
Manchmal kann es hilfreich, stimmen mit Fokus Codeanalyse und weiterhin nutzen der Visual Studio-IDE zu sein. Im folgenden finden ein Beispielszenario, die bei großen Projekten Buildzeit sparen und Filterergebnisse erleichtern verwendet werden kann:

1.  Legen Sie in der Befehlsshell die `esp.extension` und `esp.annotationbuildlevel` Umgebungsvariablen.
2.  Starten Sie Visual Studio über die Befehlsshell auf diese Variablen erben.
3.  Laden Sie Ihr Projekt, und öffnen Sie seine Eigenschaften.
4.  Aktivieren Sie Codeanalyse, wählen Sie die entsprechenden Regelsätze, aber aktivieren Sie Analysis codeerweiterungen nicht.
5.  Wechseln Sie zu der Datei, die Sie verwenden möchten, analysieren Sie die C++-Core-Richtlinien aus, und öffnen Sie seine Eigenschaften.
6.  Wählen Sie **C / C ++ \Command Befehlszeilenoptionen** und hinzufügen`/analyze:plugin EspXEngine.dll`
7.  Deaktivieren Sie die Verwendung des vorkompilierten Headers (**C / C ++ \Precompiled Header**). Dies ist notwendig, da das Modul Erweiterungen versuchen, seine interne Informationen aus der vorkompilierte Header (PCH); lesen die PCH mit Standard-Projektoptionen kompiliert, wird er nicht kompatibel sein.
8.  Erstellen Sie das Projekt neu. Die allgemeine PREFast Überprüfungen sollten auf alle Dateien ausgeführt werden. Da die C++-Core-Richtlinien aus standardmäßig nicht aktiviert ist, sollte es nur auf die Datei ausführen, für dessen Verwendung konfiguriert ist.

## <a name="how-to-use-the-c-core-guidelines-checker-outside-of-visual-studio"></a>Gewusst wie: Verwenden der C++-Kern Richtlinien Checker außerhalb von Visual Studio
Sie können die Richtlinien für C++-Core-Überprüfungen in automatisierten Builds verwenden.

### <a name="msbuild"></a>MSBuild
 Die Analyse für systemeigenen Code Checker (PREfast) ist in der MSBuild-Umgebung durch benutzerdefinierte zieledateien integriert. Sie können Projekteigenschaften verwenden, um ihn zu aktivieren und die C++-Kern Richtlinien Checker (dem PREfast basiert) hinzufügen:

 ```xml
  <PropertyGroup>
    <EnableCppCoreCheck>true</EnableCppCoreCheck>
    <CodeAnalysisRuleSet>CppCoreCheckRules.ruleset</CodeAnalysisRuleSet>¬¬
    <RunCodeAnalysis>true</RunCodeAnalysis>
  </PropertyGroup>
```
Stellen Sie sicher, dass Sie diese Eigenschaften vor dem Importieren der Datei Microsoft.Cpp.targets hinzufügen. Wählen bestimmte Regelsätze oder Erstellen eines benutzerdefinierten Regelsatzes, oder verwenden die Standard-Regelsatz, der anderen PREfast Überprüfungen enthält.

Sie können C++-Core-Überprüfungsprogramm nur für bestimmte Dateien ausführen, indem Sie die gleiche Weise wie [weiter oben beschriebenen](#coreckeck_per_file), aber mithilfe von MSBuild-Dateien. Die Umgebungsvariablen können festgelegt werden, mithilfe der `BuildMacro` Element:

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

Wenn Sie die Projektdatei ändern möchten, können Sie Eigenschaften in der Befehlszeile übergeben:

```cmd
msbuild /p:EnableCppCoreCheck=true /p:RunCodeAnalysis=true /p:CodeAnalysisRuleSet=CppCoreCheckRules.ruleset ...
```

### <a name="non-msbuild-projects"></a>Nicht-MSBuild-Projekten
Wenn Sie ein Buildsystem verwenden, die nicht auf MSBuild angewiesen können Sie weiterhin das Überprüfungsprogramm ausgeführt, aber Sie müssen einige Besonderheiten der Konfiguration des Datenbankmoduls "Codeanalyse" vertraut. Beachten Sie, dass diese Mechanismen nicht garantiert werden kann, in der Zukunft unterstützt werden müssen.

Sie müssen einige Umgebungsvariablen festgelegt und die entsprechende Befehlszeilenoptionen für den Compiler verwenden. Es ist besser, unter der "Native Tools-Eingabeaufforderung" Umgebung arbeiten, damit Sie nicht zum Suchen nach bestimmten Pfaden für den Compiler, Verzeichnisse, usw. enthalten.

1.  **Umgebungsvariablen**
  - `set esp.extensions=cppcorecheck.dll`Dies teilt das Modul die Richtlinien für C++-Core-Modul nicht laden.
  - `set esp.annotationbuildlevel=ignore`Dadurch werden die Logik, die SAL-Anmerkungen verarbeitet deaktiviert. Anmerkungen wirken sich nicht auf die Codeanalyse in die C++-Core-Richtlinien aus, aber ihre Verarbeitung dauert Zeit (in einigen Fällen viel Zeit). Diese Einstellung ist optional, jedoch dringend empfohlen.
  - `set caexcludepath=%include%`Es wird dringend empfohlen, dass Sie Warnungen deaktivieren, die Auslösen von Standardheader. Sie können mehrere Pfade hier z. B. den Pfad zu die allgemeinen Header in Ihrem Projekt hinzufügen.
2.  **Befehlszeilenoptionen**
  - `/analyze`Aktiviert die Codeanalyse (auch erwägen / analyze: nur und / analyze: stillen).
  - `/analyze:plugin EspXEngine.dll`Diese Option lädt das Erweiterungen durch Code Analysis-Modul in die PREfast. Dieses Modul lädt wiederum die C++-Core-Richtlinien aus.



## <a name="use-the-guideline-support-library"></a>Verwenden Sie die Richtlinie-Unterstützungsbibliothek  
 Die Richtlinie Unterstützungsbibliothek dient lassen sich die zentralen Richtlinien befolgen. GSL enthält Definitionen, die Sie als fehleranfällig Konstrukte gegen sicherer alternativen austauschen können. Ersetzen Sie z. B. eine `T*, length` -Paar von Parametern mit dem `span<T>` Typ. GSL finden Sie unter [http://www.nuget.org/packages/Microsoft.Gsl](http://www.nuget.org/packages/Microsoft.Gsl). Die Bibliothek ist als open Source-, damit Sie die Datenquellen anzeigen, Kommentare oder beitragen können. Das Projekt finden Sie unter [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

 ## <a name="vs2015_corecheck"></a>Verwenden Sie die Richtlinien C++ Core überprüfen in Visual Studio 2015-Projekten  
  Wenn Sie Visual Studio 2015 verwenden, werden die C++ Core überprüfen Code Codeanalyse-Regelsätze nicht standardmäßig installiert. Sie müssen einige zusätzliche Schritte ausführen, bevor Sie die C++-Kern überprüfen Codeanalysetools in Visual Studio 2015 aktivieren können. Microsoft bietet Support für Visual Studio 2015-Projekten mithilfe von NuGet-Paket. Das Paket wird mit der Bezeichnung Microsoft.CppCoreCheck, und es finden Sie unter [http://www.nuget.org/packages/Microsoft.CppCoreCheck](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Dieses Paket erfordert, dass Sie mindestens Visual Studio 2015 mit Update 1 installiert haben.  
  
 Das Paket wird auch ein anderes Paket als eine Abhängigkeit, die eine reine Richtlinie Support Library (GSL) installiert. GSL steht auch auf GitHub unter [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).  

 Aufgrund der Art und Weise Codeanalyseregeln geladen wurden, müssen Sie das Microsoft.CppCoreCheck NuGet-Paket in jeder C++-Projekt installieren, die Sie in Visual Studio 2015 überprüfen möchten.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project-in-visual-studio-2015"></a>Das Projekt in Visual Studio 2015 das Microsoft.CppCoreCheck-Paket hinzu  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste auf das Kontextmenü des Projekts in der Projektmappe zu öffnen, die Sie das Paket hinzufügen möchten. Wählen Sie **NuGet-Pakete verwalten** So öffnen die **NuGet Package Manager**.  
  
2.  In der **NuGet Package Manager** Fenster, suchen Sie nach Microsoft.CppCoreCheck.  
  
     ![NuGet-Paket-Manager-Fenster zeigt CppCoreCheck Paket](../code-quality/media/cppcorecheck_nuget_window.PNG "CPPCoreCheck_Nuget_Window")  
  
3.  Wählen Sie das Paket Microsoft.CppCoreCheck, und wählen Sie dann die **installieren** Schaltfläche, um die Regeln zum Projekt hinzuzufügen.  
  
 Das NuGet-Paket Fügt eine zusätzliche MSBuild *targets* Datei dem Projekt ein, der aufgerufen wird, wenn Sie die Codeanalyse für Ihr Projekt aktivieren. Dies *targets* Datei fügt die Regeln C++ Core überprüfen als zusätzliche Erweiterung zu Visual Studio-Codeanalysetools. Wenn das Paket installiert ist, können Sie das Dialogfeld "Eigenschaftenseiten" So aktivieren oder Deaktivieren von Regeln für die freigegebenen und experimentellen verwenden.  

## <a name="see-also"></a>Siehe auch
[Referenz zu Visual Studio C++ Core Kontrollkästchen](code-analysis-for-cpp-corecheck.md).
  
