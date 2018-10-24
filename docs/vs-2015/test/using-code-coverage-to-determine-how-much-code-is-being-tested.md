---
title: Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code coverage
ms.assetid: 800fc739-acd2-4242-84cb-1d83b4d82cf9
caps.latest.revision: 38
ms.author: gewarren
manager: douge
ms.openlocfilehash: adeca654f14fd068c7ce1cb042e57dbc3891cbf4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834057"
---
# <a name="using-code-coverage-to-determine-how-much-code-is-being-tested"></a>Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie den Anteil des Projektcodes ermitteln möchten, der in codierten Tests wie Komponententests tatsächlich getestet wird, verwenden Sie die Code Coverage-Funktion von Visual Studio. Um sich effektiv vor Fehlern zu schützen, sollten Sie die Tests für den Großteil Ihres Codes ausführen bzw. diesen "abdecken".  
  
 Die Codeabdeckungsanalyse kann sowohl in verwaltetem (CLI) als auch in nicht verwaltetem (systemeigenen) Code angewendet werden.  
  
 Sie sollten die Codeabdeckung verwenden, wenn Sie Testmethoden mit dem Test-Explorer ausführen. In der Ergebnistabelle wird der Prozentsatz des Codes angegeben, der in den einzelnen Assemblys, Klassen und Methoden ausgeführt wurde. Außerdem wird im Quellcode-Editor angezeigt, welcher Code getestet wurde.  
  
 ![Code Coverage-Ergebnisse mit Färbung](../test/media/codecoverage1.png "CodeCoverage1")  
  
 **Anforderungen**  
  
-   Visual Studio Enterprise  
  
### <a name="to-analyze-code-coverage-on-unit-tests-in-test-explorer"></a>So analysieren Sie die Code Coverage in Komponententests im Test-Explorer  
  
1.  Wählen Sie im Menü **Test** die Option **Code Coverage analysieren** aus.  
  
2.  Um anzuzeigen, welche Zeilen ausgeführt wurden, wählen Sie ![„Code Coverage-Färbung anzeigen“-Symbol](../test/media/codecoverage-showcoloringicon.png "CodeCoverage-ShowColoringIcon")**Code Coverage-Färbung anzeigen**.  
  
     Um die Farben zu ändern oder den Text fett formatiert anzuzeigen, wählen Sie **Extras**, **Optionen**, **Umgebung**, **Schriftarten und Farben** und **Einstellungen anzeigen für: Text-Editor** aus. Unter **Elemente anzeigen** können Sie die Abdeckungselemente anpassen.  
  
3.  Wenn die Ergebnisse eine niedrige Abdeckung anzeigen, untersuchen Sie, welche Teile des Codes nicht ausgeführt werden, und schreiben Sie weitere Tests, um diese abzudecken. Entwicklungsteams streben normalerweise eine Codeabdeckung von ca. 80 % an. In einigen Situationen ist eine geringere Abdeckung akzeptabel. Beispielsweise ist eine geringere Abdeckung akzeptabel, wenn ein Teil des Codes aus einer Standardvorlage generiert wird.  
  
> [!TIP]
>  So erhalten Sie genaue Ergebnisse:  
> 
> - Überprüfen Sie, ob Compileroptimierung deaktiviert ist.  
> 
>   Wenn Sie mit nicht verwaltetem (systemeigenen) Code arbeiten, verwenden Sie einen Debugbuild.  
>   -   Stellen Sie sicher, dass Sie für jede Assembly PDB-Dateien (Symboldateien) generieren.  
> 
>   Sollten Sie nicht die erwarteten Ergebnisse erhalten, finden Sie weitere Informationen unter [Problembehandlung bei der Codeabdeckung](../test/troubleshooting-code-coverage.md). sein. Vergessen Sie nicht, die Codeabdeckung nach Aktualisierung des Codes erneut auszuführen. Abdeckungsergebnisse und Codefarbe werden nach Änderung des Codes oder der Ausführung von nicht automatisch aktualisiert.  
  
## <a name="reporting-in-blocks-or-lines"></a>Berichterstellung in Blöcken oder in Zeilen  
 Die Codeabdeckung wird in *Blöcken* gezählt. Ein Block ist ein Stück Code mit genau einem Einstiegs- und Endpunkt.  Wenn die Ablaufsteuerung des Programms einen Block während eines Testlaufs durchläuft, wird dieser Block als abgedeckt gezählt. Wie oft der Block verwendet wird, hat keinen Einfluss auf das Ergebnis.  
  
 Die Ergebnisse können auch auf Zeilen bezogen angezeigt werden, wenn Sie in der Tabellenkopfzeile **Spalten hinzufügen/entfernen** auswählen. Werden im Testlauf alle Codeblöcke einer beliebigen Codezeile ausgeführt, zählt dies als eine Zeile. Wenn eine Zeile Codeblöcke enthält, von denen einige ausgeführt werden und andere nicht, zählt dies als Teilzeile.  
  
 Manche Benutzer bevorzugen die Zählung in Zeilen, da die Prozentsätze genauer der Größe der Fragmente entsprechen, die im Quellcode angezeigt werden. Ein langer Block mit Berechnungen zählt als ein einzelner Block, selbst wenn er viele Zeilen einnimmt.  
  
## <a name="managing-code-coverage-results"></a>Verwalten von Codeabdeckungsergebnissen  
 Im Fenster "Codeabdeckungsergebnisse" wird normalerweise das Ergebnis der letzten Ausführung angezeigt. Die Ergebnisse ändern sich, wenn Sie die Testdaten ändern oder jeweils nur einige Tests ausführen.  
  
 Das Fenster "Codeabdeckung" kann auch zur Anzeige von vorherigen Ergebnissen oder von Ergebnissen verwendet werden, die über andere Computer abgerufen wurden.  
  
 Sie können die Ergebnisse aus mehreren Testläufen zusammenführen, zum Beispiel aus Testläufen, in denen unterschiedliche Testdaten verwendet werden.  
  
-   **Um ein vorheriges Resultset aufzurufen**, wählen Sie dieses aus dem Dropdownmenü aus. Das Menü enthält eine temporäre Liste, die gelöscht wird, wenn Sie eine neue Projektmappe öffnen.  
  
-   **Um Ergebnisse aus einer vorherigen Sitzung aufzurufen**, wählen Sie **Codeabdeckungsergebnisse importieren** aus, navigieren Sie zum Ordner „TestResults“ in der Projektmappe, und importieren Sie eine COVERAGE-Datei.  
  
     Die Codeabdeckungsfärbung ist möglicherweise falsch, wenn der Quellcode nach Generieren der COVERAGE-Datei geändert wurde.  
  
-   **Um die Ergebnisse als Text lesbar zu machen**, wählen Sie **Codeabdeckungsergebnisse exportieren** aus. Dadurch wird eine lesbare COVERAGEXML-Datei generiert, die mit anderen Tools verarbeitet oder problemlos in einer E-Mail gesendet werden kann.  
  
-   **Um Ergebnisse an eine andere Person weiterzuleiten**, senden Sie dieser entweder eine COVERAGE-Datei oder eine exportierte COVERAGEXML-Datei. Die Datei kann dann importiert werden. Verfügt die andere Person über dieselbe Version des Quellcodes, kann sie die Abdeckungsfärbung sehen.  
  
## <a name="merging-results-from-different-runs"></a>Zusammenführen von Ergebnissen aus verschiedenen Ausführungen  
 In einigen Situationen werden abhängig von den Testdaten andere Blöcke im Code verwendet. Daher sollten Sie die Ergebnisse aus verschiedenen Testläufen kombinieren.  
  
 Bei einem Test mit der Eingabe "2 " stellen Sie beispielsweise fest, dass 50 % einer bestimmten Funktion abgedeckt werden. Wenn Sie den Test ein zweites Mal mit der Eingabe "– 2 " ausführen, sehen Sie in der Ansicht der Abdeckungsfärbung, dass die anderen 50 % der Funktion abgedeckt werden. Führen Sie nun die Ergebnisse aus den zwei Testläufen zusammen. Die Berichtsansicht und die Ansicht der Abdeckungsfärbung zeigen nun an, dass 100 % der Funktion ausgeführt wurden.  
  
 Verwenden Sie hierzu das ![Symbol für die Schaltfläche „Zusammenführen“ im Fenster „Codeabdeckung“](../test/media/codecoverage-mergeicon.png "CodeCoverage-MergeIcon")**Codeabdeckungsergebnisse zusammenführen**. Sie können eine beliebige Kombinationen aus den letzten Testläufen oder aus importierten Ergebnissen auswählen. Wenn Sie exportierte Ergebnisse kombinieren möchten, müssen Sie diese zuerst importieren.  
  
 Speichern Sie die Ergebnisse eines Zusammenführungsvorgangs mithilfe der Option **Export Code Coverage Results** (Codeabdeckungsergebnisse exportieren).  
  
### <a name="limitations-in-merging"></a>Einschränkungen beim Zusammenführen  
  
-   Wenn Sie Abdeckungsdaten aus verschiedenen Versionen desselben Codes zusammenführen, werden die Ergebnisse separat dargestellt und sind nicht kombiniert. Um vollständig kombinierte Ergebnisse zu erhalten, verwenden Sie denselben Build des Codes, und ändern Sie nur die Testdaten.  
  
-   Wenn Sie eine Ergebnisdatei zusammenführen, die exportiert und anschließend importiert wurde, können Sie die Ergebnisse nur nach Zeilen und nicht nach Blöcken anzeigen. Verwenden Sie den Befehl **Spalten hinzufügen/entfernen**, um die Zeilendaten anzuzeigen.  
  
-   Wenn Sie Ergebnisse aus Tests für ein ASP.NET-Projekt zusammenführen, werden die Ergebnisse für die separaten Tests angezeigt und sind nicht kombiniert. Dies gilt nur für ASP.NET-Artefakte selbst: Die Ergebnisse für alle anderen Assemblys werden kombiniert dargestellt.  
  
## <a name="excluding-elements-from-the-code-coverage-results"></a>Ausschließen von Elementen aus den Codeabdeckungsergebnissen  
 Sie können bestimmte Elemente im Code aus den Abdeckungsergebnissen ausschließen, zum Beispiel, wenn der Code aus einer Textvorlage generiert wird. Fügen Sie das `System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverage`-Attribut zu einem der folgenden Codeelemente hinzu: Klasse, Struktur, Methode, Eigenschaft-Setter oder -Getter oder Ereignis. Beachten Sie, dass durch das Ausschließen einer Klasse nicht deren abgeleitete Klassen ausgeschlossen werden.  
  
 Zum Beispiel:  
  
```csharp  
  
using System.Diagnostics.CodeAnalysis;   
...  
public class ExampleClass1  
{   
    [ExcludeFromCodeCoverage]  
    void ExampleMethod() {...}  
  
    [ExcludeFromCodeCoverage] // exclude property  
    int ExampleProperty1   
    { get {...} set{...}}  
  
    int ExampleProperty2  
    {  
        get  
        {  
            ...  
        }  
        [ExcludeFromCodeCoverage] // exclude setter  
        set  
        {  
            ...  
        }  
    }  
  
}  
[ExcludeFromCodeCoverage]  
class ExampleClass2 { ... }  
  
```  
  
```vb  
Imports System.Diagnostics.CodeAnalysis  
  
Class ExampleClass1          
    <ExcludeFromCodeCoverage()>  
    Public Sub ExampleSub1()  
        ...  
    End Sub  
  
    ' Exclude property  
    < ExcludeFromCodeCoverage()>  
    Property ExampleProperty1 As Integer  
        ...  
    End Property  
  
    ' Exclude setter  
    Property ExampleProperty2 As Integer  
        Get  
            ...  
        End Get  
        <ExcludeFromCodeCoverage()>  
        Set(ByVal value As Integer)  
            ...  
        End Set  
    End Property  
End Class  
  
<ExcludeFromCodeCoverage()>  
Class ExampleClass2  
...  
End Class  
  
```  
  
```cpp#  
// A .cpp file compiled as managed (CLI) code.  
using namespace System::Diagnostics::CodeAnalysis;  
...  
public ref class ExampleClass1  
{  
  public:  
    [ExcludeFromCodeCoverage]  
    void ExampleFunction1() { ... }  
  
    [ExcludeFromCodeCoverage]  
    property int ExampleProperty2 {...}  
  
    property int ExampleProperty2 {  
      int get() { ... }  
     [ExcludeFromCodeCoverage]  
      void set(int value) { ...  }  
   }  
  
}  
  
[ExcludeFromCodeCoverage]  
public ref class ExampleClass2  
{ ... }  
  
```  
  
### <a name="excluding-elements-in-native-c-code"></a>Ausschließen von Elementen im systemeigenen C++-Code  
 So schließen Sie nicht verwaltete (systemeigene) Elemente im C++-Code aus:  
  
```cpp  
  
#include <CodeCoverage\CodeCoverage.h>  
...  
  
// Exclusions must be compiled as unmanaged (native):  
#pragma managed(push, off)  
  
// Exclude a particular function:  
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");  
  
// Exclude all the functions in a particular class:  
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");  
  
// Exclude all the functions generated from a particular template:   
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");  
  
// Exclude all the code from a particular .cpp file:  
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");  
  
// After setting exclusions, restore the previous managed/unmanaged state:  
#pragma managed(pop)  
  
```  
  
 Verwenden Sie folgende Makros:  
  
 `ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`  
  
 `ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`  
  
-   *ExclusionName* ist ein eindeutiger Name.  
  
-   *FunctionName* ist ein vollqualifizierter Funktionsname. Er enthält möglicherweise Platzhalter. Um beispielsweise alle Funktionen einer Klasse auszuschließen, schreiben Sie `MyNamespace::MyClass::*`  
  
-   *SourceFilePath* ist der lokale oder UNC-Pfad einer CPP-Datei. Er enthält möglicherweise Platzhalter. Im folgenden Beispiel werden alle Dateien in einem bestimmten Verzeichnis ausgeschlossen: `\\MyComputer\Source\UnitTests\*.cpp`  
  
-   `#include <CodeCoverage\CodeCoverage.h>`  
  
-   Platzaufrufe zu den Ausschlussmakros im globalen Namespace, nicht innerhalb eines Namespace oder einer Klasse.  
  
-   Sie können die Ausschlüsse entweder in der Komponententestcodedatei oder in der Anwendungscodedatei platzieren.  
  
-   Die Ausschlüsse müssen als nicht verwalteter (systemeigener) Code kompiliert werden, indem Sie entweder die Compileroption festlegen oder `#pragma managed(off)` verwenden.  
  
> [!NOTE]
>  Um Funktionen in C++/CLI-Code auszuschließen, wenden Sie das Attribut `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` auf die Funktion an. Dasselbe gilt für C#.  
  
### <a name="including-or-excluding-additional-elements"></a>Ein- oder Ausschließen zusätzlicher Elemente  
 Die Codeabdeckungsanalyse wird nur für geladene Assemblys ausgeführt, für die eine PDB-Datei in demselben Verzeichnis verfügbar ist, in dem sich die DLL- oder EXE-Datei befindet. Daher können Sie in bestimmten Fällen den Satz der enthaltenen Assemblys erweitern, indem Sie Kopien der entsprechenden PDB-Dateien abrufen.  
  
 Sie können besser steuern, welche Assemblys und Elemente für die Codeabdeckungsanalyse ausgewählt werden, indem Sie eine RUNSETTINGS-Datei schreiben. Beispielsweise können Sie Assemblys bestimmter Arten ausschließen, ohne deren Klassen Attribute hinzuzufügen. Weitere Informationen finden Sie unter [Anpassen der Codeabdeckungsanalyse](../test/customizing-code-coverage-analysis.md).  
  
## <a name="analyzing-code-coverage-in-the-build-service"></a>Analysieren der Code Coverage im Builddienst  
 Wenn Sie Code einchecken, werden Ihre Tests zusammen mit allen anderen Tests von anderen Teammitgliedern auf dem Buildserver ausgeführt. (Wenn Sie dies noch nicht eingerichtet haben, finden Sie unter [Ausführen von Tests im Buildprozess](http://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38) Informationen hierzu.) Es ist hilfreich, die Code Coverage für den Builddienst zu analysieren, da Sie dadurch das aktuellste und umfassendste Bild der Code Coverage für das gesamte Projekt erhalten. Dazu gehören auch automatisierte Systemtests und andere codierte Tests, die Sie normalerweise nicht auf Entwicklungscomputern ausführen.  
  
1. Öffnen Sie im Team Explorer **Builds**, und fügen Sie dann eine Builddefinition hinzu oder bearbeiten Sie diese.  
  
2. Erweitern Sie auf der Seite **Prozess** die Elemente **Automatisierte Tests**, **Testquelle** und **Testlaufeinstellungen**. Legen Sie die Option **Code Coverage Enabled**(Code Coverage aktiviert) für den **Type of Run Settings File**(Typ der Laufzeiteinstellungsdatei) fest.  
  
    Wenn Sie über mehrere Testquelldefinitionen verfügen, wiederholen Sie diesen Schritt für jede einzelne Definition.  
  
   - <em>Es ist jedoch kein Feld mit dem Namen **ausführen Einstellungen Dateityp</em>*. *  
  
      Wählen Sie **Testassembly** unter **Automatisierte Tests**, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten **[...]** am Ende der Zeile. Wählen Sie unter **Test Runner** im Dialogfeld **Testlauf hinzufügen/bearbeiten** die Option **Visual Studio Test Runner** aus.  
  
   ![Festlegen der Builddefinition für Code Coverage](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")  
  
   Nach Ausführung des Builds werden die Code Coverage-Ergebnisse an den Testlauf angefügt und in der Buildzusammenfassung angezeigt.  
  
## <a name="analyzing-code-coverage-in-a-command-line"></a>Analysieren der Codeabdeckung in einer Befehlszeile  
 Um Tests über die Befehlszeile auszuführen, verwenden Sie "vstest.console.exe". Die Code Coverage ist eine Option in diesem Hilfsprogramm. Weitere Informationen finden Sie unter [Befehlszeilenoptionen von „VSTest.Console.exe“](http://msdn.microsoft.com/library/52e1689d-b1a8-4589-bd98-99a55acd0a11).  
  
1.  Starten der Visual Studio Developer-Eingabeaufforderung:  
  
     Wählen Sie im Windows-Menü **Start** nacheinander **Alle Programme**, **Microsoft Visual Studio**, **Visual Studio-Tools** und **Developer-Eingabeaufforderung** aus.  
  
2.  Führen Sie Folgendes aus:  
  
     `vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage`  
  
## <a name="troubleshooting"></a>Problembehandlung  
 Wenn Sie keine Codeabdeckungsergebnisse sehen, lesen Sie [Problembehandlung bei der Codeabdeckung](../test/troubleshooting-code-coverage.md).  
  
## <a name="external-resources"></a>Externe Ressourcen  
  
### <a name="guidance"></a>Empfehlungen  
 [Testing for Continuous Delivery with Visual Studio 2012 – Chapter 2: Unit Testing: Testing the Inside (Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests)](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassen der Code Coverage-Analyse](../test/customizing-code-coverage-analysis.md)   
 [Problembehandlung bei der Codeabdeckung](../test/troubleshooting-code-coverage.md)   
 [Komponententest für Code](../test/unit-test-your-code.md)



