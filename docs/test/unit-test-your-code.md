---
title: "Komponententest f&#252;r Code | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Testen von Code, Automatisierte Tests"
  - "Komponententests, Überprüfen von Code mit"
  - "Visual Studio, Komponententests"
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 62
caps.handback.revision: 62
ms.author: "mlearned"
manager: "douge"
---
# Komponententest f&#252;r Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit Komponententests können Entwickler und Tester die Methoden der Klassen in [!INCLUDE[csharp_current_short](../misc/includes/csharp_current_short_md.md)]\-, [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]\- und [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)]\-Projekten schnell auf logische Fehler überprüfen.  
  
 Zu den Komponententest\-Tools gehören:  
  
1.  **Test\-Explorer.** Mit dem Test\-Explorer können Sie Komponententests ausführen und deren Ergebnisse anzeigen.  Der Test\-Explorer erlaubt die Verwendung jedes Komponententest\-Frameworks, auch Frameworks von Drittanbietern, die über einen Adapter für den Explorer verfügen.  
  
2.  **Microsoft\-Komponententest\-Framework für verwalteten Code.** Das Microsoft\-Komponententest\-Framework für verwalteten Code wird mit Visual Studio installiert und stellt ein Framework zum Testen von .NET\-Code bereit.  
  
3.  **Microsoft\-Komponententest\-Framework für C\+\+.** Das Microsoft\-Komponententest\-Framework für C\+\+ wird mit Visual Studio installiert und stellt ein Framework zum Testen von systemeigenen Code bereit.  
  
4.  **Codeabdeckungstools.** Sie können die Menge an Produktcode bestimmen, die Ihre Komponententests nach der Eingabe eines Befehls im Test\-Explorer prüfen.  
  
5.  **Microsoft Fakes\-Isolationsframework.** Das Microsoft Fakes\-Isolationsframework kann Ersatzklassen und Methoden für Produktions\- und Systemcode erstellen, der Abhängigkeiten im getesteten Code erstellt.  Durch die Implementierung von Fakedelegaten für eine Funktion können Sie das Verhalten und die Ausgabe des Abhängigkeitsobjekts steuern.  
  
 Sie können auch [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) verwenden, um Ihren .NET\-Code zum Generieren von Testdaten und einer Suite von Komponententests zu untersuchen.  Für jede Anweisung im Code wird eine Testeingabe generiert, die die betreffende Anweisung ausführt.  Für jede bedingte Verzweigung im Code wird eine Fallanalyse ausgeführt.  
  
## Hauptaufgaben  
 Lesen Sie folgende Themen, um Komponententests besser zu verstehen und sie zu erstellen:  
  
|Aufgaben|Verwandte Themen|  
|--------------|----------------------|  
|**Schnellstarts und exemplarischen Vorgehensweisen:** Erfahren Sie in den folgenden Themen ausgehend von Codebeispielen, wie Komponententests in Visual Studio durchgeführt werden.|-   [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Schnellstart: Testgesteuerte Entwicklung mit dem Test\-Explorer](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Hinzufügen von Komponententests zu vorhandenen C\+\+\-Anwendungen](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Unit testing native code with Test Explorer](http://msdn.microsoft.com/de-de/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|  
|**Komponententest mit Test\-Explorer:** Erfahren Sie, wie Sie Test\-Explorer unterstützen kann, produktivere und effizientere Komponententests zu erstellen.|-   [Grundlagen zum Komponententest](../test/unit-test-basics.md)<br />-   [Ein Komponententestprojekt erstellen](../test/create-a-unit-test-project.md)<br />-   [Ausführen von Komponententests mit dem Test\-Explorer](../test/run-unit-tests-with-test-explorer.md)<br />-   [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md)<br />-   [Upgrading Unit Tests from Visual Studio 2010](http://msdn.microsoft.com/de-de/9bb75856-f68a-4de2-a084-b08a947a1172)|  
|**Komponententest von verwaltetem Code:**|-   [Schreiben von Komponententests für .NET Framework mit dem Microsoft\-Komponententestframework für verwalteten Code](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|  
|**Komponententest von C\+\+\-Code**|-   [Schreiben von Komponententests für C\/C\+\+ mit dem Microsoft\-Unittest\-Framework für C\+\+](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|  
|**Isolation von Komponententests**|-   [Isolieren von getestetem Code mithilfe von Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md)|  
|**Verwenden Sie die Codeabdeckung, um zu identifizieren, welcher Teil des Projektcodes mit Komponententests getestet wird:** Erfahren Sie mehr über die Codeabdeckungsfunktion der [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]\-Testtools.|-   [Bestimmen des Umfangs des zu testenden Codes mithilfe von Codeabdeckung](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|  
|**Führen Sie die Belastungs\- und Leistungsanalyse mithilfe von Auslastungstests für die Komponententests aus:** Sie können einen Auslastungstest erstellen und diesem die Komponententests hinzufügen, um die Leistungs\- und Auslastungsprobleme in der Anwendung isolieren zu können. **Note:**  Zum Erstellen und Verwenden von Auslastungstests ist Visual Studio Enterprise erforderlich.|-   [Erstellen und Bearbeiten von Auslastungstests](http://msdn.microsoft.com/de-de/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Vorgehensweise: Hinzufügen von Webleistungstests und Komponententests zu einem Auslastungstestszenario](http://msdn.microsoft.com/de-de/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Vorgehensweise: Entfernen von Webleistungstests und Komponententests aus einem Auslastungstestszenario](http://msdn.microsoft.com/de-de/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|  
|**Legen Sie Quality Gates fest und erzwingen Sie diese:** Sie können Quality Gates erstellen, um zu erzwingen, dass vor dem Einchecken von Code Tests ausgeführt werden. Auf diese Weise können Sie die Qualität des Codes sicherstellen.|-   [Set and Enforce Quality Gates](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)|  
|**Erweitern Sie den Komponententesttyp:** Sie können den Tests Funktionen hinzufügen, die im Komponententest\-Framework möglicherweise nicht enthalten sind.  Sie können z. B. eine Testeigenschaft hinzufügen, die angibt, ob ein Test als normaler Benutzer ausgeführt werden soll.  Sie können das Framework auch erweitern, indem Sie einer Methode Zeilenattribute hinzufügen und die Daten in dieser Zeile im Test verwenden.|Auf der folgenden [Microsoft\-Website](http://go.microsoft.com/fwlink/?LinkId=185591) finden Sie Beispielcode dahingehend, wie Sie das Komponententest\-Framework erweitern können.|  
|**Festlegen von Testoptionen:** Sie können beispielsweise angeben, an welchem Ort die Testergebnisse gespeichert werden.|[Konfigurieren von Komponententests mithilfe einer .runsettings\-Datei](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|  
  
## Verwandte Aufgaben  
 [Reviewing Test Results in Microsoft Test Manager](http://msdn.microsoft.com/de-de/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)  
  
 Beschreibt Testergebnisse und verschiedene Arten, mit diesen zu arbeiten, darunter das Anzeigen, Speichern und Löschen dieser Ergebnisse.  
  
 [Ausführen von Systemtests mit Microsoft Visual Studio](/devops-test-docs/test/running-automated-tests-using-microsoft-visual-studio)  
  
 Enthält Links zu Informationen zum Ausführen automatisierter Tests mithilfe von Visual Studio anstelle von [!INCLUDE[TCMext](../modeling/includes/tcmext_md.md)].  
  
## Verweis  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>  
 Beschreibt den UnitTesting\-Namespace, der Attribute, Ausnahmen, Asserts und andere Klassen bereitstellt, die Komponententests unterstützen.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web>  
 Beschreibt den UnitTesting.Web\-Namespace, der den UnitTesting\-Namespace durch die Unterstützung für [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] und Webdienst\-Komponententests erweitert.  
  
## Externe Ressourcen  
  
### Videos  
 [Kanal 9: Testen Ihrer mithilfe von XAML erstellten Windows Store\-Apps](http://go.microsoft.com/fwlink/?LinkId=226285)  
  
### Foren  
 [Komponententests in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=224477)  
  
### Leitfaden  
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
### Verweis  
 [Content Index for Unit Tests \(auf Englisch\)](http://go.microsoft.com/fwlink/?LinkID=254719)  
  
## Siehe auch  
 [Verbessern der Codequalität](../test/improve-code-quality.md)   
 [Testen der Anwendung](/devops-test-docs/test/test-apps-early-and-often)