---
title: Komponententests in Visual Studio| Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: f8b2ec475a4c9d8cf5799c6f429519704329c2cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="unit-test-your-code"></a>Ausführen von Komponententests für Code

Mit Komponententests können Entwickler und Tester die Methoden der Klassen in C#-, Visual Basic- und C++-Projekten schnell auf logische Fehler überprüfen.

Zu den Komponententest-Tools gehören:

* **Test-Explorer**&mdash;Mit dem **Test-Explorer** können Sie Komponententests ausführen und die Ergebnisse anzeigen. Dabei können Sie jedes Komponententest-Framework verwenden, auch Frameworks von Drittanbietern, das über einen Adapter für den **Test-Explorer** verfügt.

* **Microsoft-Komponententest-Framework für verwalteten Code**&mdash;Das Microsoft-Komponententest-Framework für verwalteten Code wird mit Visual Studio installiert und stellt ein Framework zum Testen von .NET-Code bereit.

* **Microsoft-Komponententest-Framework für C++**&mdash;Das Microsoft-Komponententest-Framework für C++ wird als Teil der Workload **Desktopentwicklung mit C++** installiert. Es stellt ein Framework zum Testen von nativem Code bereit. Google Test-, Boost.Test- und CTest-Frameworks sind ebenfalls integriert, und Adapter von Drittanbietern sind für zusätzliche Testframeworks verfügbar. Weitere Informationen finden Sie unter [Schreiben von Komponententests für C/C++ ](../test/writing-unit-tests-for-c-cpp.md).

* **Code Coverage-Tools**&mdash;Sie können die Menge an Produktcode bestimmen, die Ihre Komponententests nach der Eingabe eines Befehls im Test-Explorer prüfen.

* **Microsoft Fakes-Isolationsframework**&mdash;Das Microsoft Fakes-Isolationsframework kann Ersatzklassen und Methoden für Produktions- und Systemcode erstellen, der Abhängigkeiten im getesteten Code erstellt. Durch die Implementierung von Fakedelegaten für eine Funktion können Sie das Verhalten und die Ausgabe des Abhängigkeitsobjekts steuern.

Sie können auch [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) verwenden, um Ihren .NET-Code zum Generieren von Testdaten und einer Sammlung von Komponententests zu untersuchen. Für jede Anweisung im Code wird eine Testeingabe generiert, die die betreffende Anweisung ausführt. Für jede bedingte Verzweigung im Code wird eine Fallanalyse ausgeführt.

## <a name="key-tasks"></a>Hauptaufgaben

Lesen Sie folgende Themen, um Komponententests besser zu verstehen und sie zu erstellen:

|Aufgaben|Verwandte Themen|
|-----------|-----------------------|
|**Schnellstarts und exemplarische Vorgehensweisen:** Erfahren Sie in den folgenden Themen ausgehend von Codebeispielen, wie Komponententests in Visual Studio durchgeführt werden.|-   [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Schnellstart: Testgesteuerte Entwicklung mit dem Test-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Hinzufügen von Komponententests zu vorhandenen C++-Anwendungen](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)|
|**Komponententest mit Test-Explorer:** Erfahren Sie, wie Sie Test-Explorer unterstützen kann, produktivere und effizientere Komponententests zu erstellen.|-   [Grundlagen zum Komponententest](../test/unit-test-basics.md)<br />-   [Ein Komponententestprojekt erstellen](../test/create-a-unit-test-project.md)<br />-   [Ausführen von Komponententests mit dem Test-Explorer](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md)|
|**Komponententests von verwaltetem Code:**|-   [Schreiben von Komponententests für .NET Framework mit dem Microsoft-Komponententestframework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Komponententests von C++-Code**|-   [Schreiben von Komponententests für C-C++ mit dem Microsoft-Komponententestframework für C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Isolation von Komponententests**|-   [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Verwenden Sie Code Coverage, um zu identifizieren, welcher Teil des Projektcodes getestet wird:** Erfahren Sie mehr über das Code Coverage-Feature der Visual Studio-Testtools.|-   [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Führen Sie die Belastungs- und Leistungsanalyse mithilfe von Auslastungstests aus:** Sie können einen Auslastungstest erstellen und diesem die Komponententests hinzufügen, um die Leistungs- und Auslastungsprobleme in der Anwendung isolieren zu können.|-   [Auslastungstest (VSTS und TFS)](/vsts/load-test/)|
|**Festlegen von Quality Gates:** Sie können Quality Gates erstellen, um zu erzwingen, dass vor dem Einchecken von Code Tests ausgeführt werden. Auf diese Weise können Sie die Qualität des Codes sicherstellen.|-   [Eincheckrichtlinien (VSTS)](/vsts/tfvc/add-check-policies)|
|**Festlegen von Testoptionen:** Sie können beispielsweise angeben, an welchem Ort die Testergebnisse gespeichert werden.|[Konfigurieren von Komponententests mithilfe einer .runsettings-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>API-Referenzdokumentation

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> beschreibt den UnitTesting-Namespace, der Attribute, Ausnahmen, Assert-Vorgänge und andere Klassen bereitstellt, die Komponententests unterstützen.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> beschreibt den UnitTesting.Web-Namespace, der den UnitTesting-Namespace durch die Unterstützung für ASP.NET- und Webdienst-Komponententests erweitert.

## <a name="see-also"></a>Siehe auch

- [Verbessern der Codequalität](/visualstudio/test/improve-code-quality)
