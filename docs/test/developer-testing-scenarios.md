---
title: Testtools für Entwickler
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b133a9ce3aa5773349260249ee80edc02d6b318b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954955"
---
# <a name="developer-testing-tools-scenarios-and-capabilities"></a>Testtools, -szenarios und -funktionen für Entwickler

Aufrechterhalten der Codeintegrität mit Unittests Visual Studio bietet eine Vielzahl an leistungsstarken Tools und Methoden, die Entwickler beim Testen von Anwendungen verwenden können.

## <a name="avoid-regressions-and-achieve-code-coverage-with-intellitest"></a>Verhindern von Regressionen und Erreichen von Code Coverage mit IntelliTest

In herkömmlichen Unittestsammlungen, stellt jeder Testfall ein Beispielszenario für die Verwendung dar, und die Assertionsanweisungen enthalten die Beziehung zwischen der Ein- und Ausgabe.  Das Überprüfen einiger dieser Szenarios mag ausreichend sein, aber erfahrenen Entwicklern ist bewusst, dass Fehler auch in gut getestetem Code vorkommen können, wenn korrekte aber nicht getestete Eingaben falsche Reaktionen auslösen.

Verbessern Sie die Abdeckung und vermeiden Sie Regressionen mit IntelliTest. Mit IntelliTest wird der Aufwand zum Erstellen und Verwalten von Unittests für neuen oder vorhandenen Code drastisch verringert.

![IntelliTest im Einsatz](media/devtest-intellitest.png)

* [Introduction to IntelliTest with Visual Studio (Einführung in IntelliTest mit Visual Studio)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20IntelliTest%20with%20Visual%20Studio%20Enterprise%202015.docx)
* [IntelliTest – One Test to rule them all (IntelliTest – Ein Test für alle)](https://blogs.msdn.microsoft.com/devops/2015/07/05/intellitest-one-test-to-rule-them-all/)
* [IntelliTest-Videos](https://channel9.msdn.com/Series/Test-Tools-in-Visual-Studio)
* [Erste Schritte mit IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest reference manual (IntelliTest-Referenzhandbuch)](intellitest-manual/index.md)

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Testen der Benutzeroberfläche mit programmierter UI und Selenium

Testen Sie Ihre Benutzeroberfläche mit branchenführenden oder von der Community als gut befundenen UI-Tests. Tests für programmierte UI bieten die Möglichkeit, vollautomatisierte Tests zu erstellen, um die Funktionalität und das Verhalten der Benutzeroberfläche Ihrer Anwendung zu überprüfen. Sie können Benutzeroberflächentests für eine Vielzahl von Technologien automatisieren, so z.B. für XAML-basierte UWP-Apps, Browser-Apps und SharePoint-Apps.

Egal, ob Sie sich für branchenführende Tests für programmierte UI oder für generische, browserbasierte UI-Tests mit Selenium entscheiden: Visual Studio stellt Ihnen alle Tools bereit, die Sie benötigen.

![Benutzeroberflächentests mit programmierter UI](media/devtest-codeduitest.png)

* [Verwenden der Benutzeroberflächenautomatisierung zum Testen des Codes](use-ui-automation-to-test-your-code.md)
* [Erstellen, Bearbeiten und Verwalten von Tests der programmierten UI](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Testen von UWP-Apps mit Tests der programmierten UI](test-uwp-app-with-coded-ui-test.md)
* [Testen von SharePoint-Anwendungen mit Tests der programmierten UI](testing-sharepoint-2010-applications-with-coded-ui-tests.md)
* [Introduction to Creating Coded UI Tests with Visual Studio Enterprise (Einführung in die Erstellung von Tests der programmierter UI mit Visual Studio Enterprise)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Introduction%20to%20Coded%20UI%20Tests%20with%20Visual%20Studio%20Enterprise%202015.docx)

## <a name="effective-unit-testing-with-visual-studio-code-coverage"></a>Effektive Unittests mit Code Coverage von Visual Studio

Wenn Sie den Anteil des Projektcodes ermitteln möchten, der in codierten Tests wie Unittests tatsächlich getestet wird, verwenden Sie die Code Coverage-Funktion von Visual Studio. Um sich effektiv vor Fehlern zu schützen, sollten Sie die Tests für den Großteil Ihres Codes ausführen bzw. diesen „abdecken“.

Die Code Coverage-Analyse kann sowohl in verwaltetem als auch in nicht verwaltetem (nativem) Code angewendet werden.

Sie sollten die Codeabdeckung verwenden, wenn Sie Testmethoden mit dem Test-Explorer ausführen. In der Ergebnistabelle wird der Prozentsatz des Codes angegeben, der in den einzelnen Assemblys, Klassen und Methoden ausgeführt wurde. Außerdem wird im Quellcode-Editor angezeigt, welcher Code getestet wurde.

* [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Unittest, Code Coverage und Codeklonanalyse mit Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Anpassen der Code Coverage-Analyse](customizing-code-coverage-analysis.md)

## <a name="test-explorer"></a>Test-Explorer

Der **Test-Explorer** hilft Entwicklern beim Erstellen, Verwalten und Ausführen von Komponententests.

![Visual Studio Team Explorer](media/devtest-testexplorer.png)

* [Erste Schritte mit Unittests](unit-test-your-code.md)
* [Ausführen von Komponententests mit dem Test-Explorer](run-unit-tests-with-test-explorer.md)
* [Häufig gestellte Fragen zum Test-Explorer](test-explorer-faq.md)
* [Installieren von Frameworks für Komponententests von Drittanbietern](install-third-party-unit-test-frameworks.md)

Visual Studio kann auch erweitert werden und ermöglicht Kompontenentestadapter von Drittanbietern wie NUnit und xUnit.net. Zusätzlich geht die Codeklonfunktion mit der Bereitstellung hochwertiger Software einher. Mit ihr können Sie Blöcke semantisch ähnlichen Codes identifizieren, die Kandidaten für gängige Fehlerbehebungen und Refactoring sein können.

![Integrationspakete von Drittanbietern](media/devtest-thirdparty.png)

## <a name="see-also"></a>Siehe auch

* [Erste Schritte mit Unittests](getting-started-with-unit-testing.md)
* [Speed up Unit Test Execution in Team Foundation Server (Beschleunigen der Ausführung von Unittests in Team Foundation Server)](https://blogs.msdn.microsoft.com/devops/2015/07/30/speeding-up-unit-test-execution-in-tfs/)
* [Parallel and context sensitive unit test execution (Parallele und kontextsensitive Ausführung von Unittests)](https://blogs.msdn.microsoft.com/devops/2016/02/08/parallel-and-context-sensitive-test-execution-with-visual-studio-2015-update-1/)
* [Unittest, Code Coverage und Codeklonanalyse mit Visual Studio (Lab)](http://download.microsoft.com/download/6/2/B/62B60ECE-B9DC-4E8A-A97C-EA261BFB935E/Docs/Unit%20Testing,%20Code%20Coverage%20and%20Code%20Clone%20Analysis%20with%20Visual%20Studio%202015.docx)
* [Schreiben von Komponententests für C/C++](writing-unit-tests-for-c-cpp.md)
