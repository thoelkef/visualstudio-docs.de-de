---
title: "Test-Explorer – häufig gestellte Fragen | Microsoft-Dokumentation"
ms.date: 1/15/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: ghogen
ms.openlocfilehash: 63c1b25ad597dc3d56dfc398ec9c6c463aec200d
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio-Test-Explorer – häufig gestellte Fragen

## <a name="test-discovery"></a>Testermittlung

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-are-dynamically-defined-for-example-theories-custom-adapters-custom-traits-ifdefs-etc-how-can-i-discover-these-tests"></a>1. Der Test-Explorer erkennt meine dynamisch definierten Tests nicht. (Z.B. Theorien, benutzerdefinierte Adapter und Merkmale oder „#ifdefs“) Wie kann ich diese Tests ermitteln?

  Erstellen Sie das Projekt, und vergewissern Sie sich, dass in **Extras > Optionen > Test** die assemblybasierte Ermittlung aktiviert ist.

  Bei der [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824) handelt es sich um eine quellenbasierte Testermittlung. Sie kann keine Tests ermitteln, die z.B. Theorien, benutzerdefinierte Adapter und Merkmale oder `#ifdef`-Anweisungen verwenden, da diese zur Laufzeit definiert werden. Ein Build ist erforderlich, damit diese Tests korrekt ermittelt werden. In den 15.6-Vorschauen wird die assemblybasierte Ermittlung (die herkömmliche Ermittlung) nur nach Builds ausgeführt. Diese Einstellung bedeutet, dass die Testermittlung in Echtzeit während der Bearbeitung so viele Tests wie möglich ermittelt, und die assemblybasierte Ermittlung das Anzeigen von dynamisch definierten Tests nach einem Build ermöglicht. Testermittlung in Echtzeit verbessert die Reaktionsfähigkeit, ermöglicht Ihnen aber dennoch, vollständige und genaue Ergebnisse nach einem Build zu erhalten.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. Was bewirkt das Symbol „+“ (Pluszeichen), das in der obersten Zeile des Test-Explorers angezeigt wird?

  Das Symbol „+“ (Pluszeichen) gibt an, dass mehr Tests nach einem Build ermittelt werden können, solange die assemblybasierte Ermittlung aktiviert ist. Es wird angezeigt, wenn dynamisch definierte Tests im Projekt erkannt werden.

  ![Plussymbol-Zusammenfassungszeile](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. Assemblybasierte Ermittlung funktioniert bei meinem Projekt nicht mehr. Wie kann ich sie wieder aktivieren?

  Wechseln Sie zu **Extras > Optionen > Test**, und aktivieren Sie das Kontrollkästchen **Nach der Builderstellung zusätzliche Tests aus erstellten Assemblys ermitteln**.

  ![Assemblybasierte Option](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Tests werden jetzt im Test-Explorer angezeigt, während ich schreibe, ohne dass ich mein Projekt erstellen muss. Was hat sich geändert?

  Dieses Feature wird als [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824) bezeichnet. Dabei wird ein Roslyn-Analysetool verwendet, um Tests zu ermitteln und den Test-Explorer in Echtzeit zu füllen, ohne dass Sie Ihr Projekt erstellen müssen. Weitere Informationen zum Verhalten der Testermittlung bei dynamisch definierten Tests wie Theorien oder benutzerdefinierten Merkmalen finden Sie in der Antwort zur ersten häufig gestellten Frage (FAQ #1).

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Welche Sprachen und Testframeworks kann die Testermittlung in Echtzeit verwenden?

  [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824) funktioniert nur für die verwalteten Sprachen (C# und Visual Basic), da sie mit dem Roslyn-Compiler erstellt wird. Derzeit funktioniert Testermittlung in Echtzeit nur für xUnit-, NUnit- und MSTest-Framework.

### <a name="6-how-can-i-turn-on-logs-for-the-test-explorer"></a>6. Wie kann ich die Protokollierung für den Test-Explorer aktivieren?

  Navigieren Sie zu **Extras > Optionen > Test**, und suchen Sie dort nach dem Protokollbereich.

### <a name="7-why-are-my-tests-in-uwp-projects-not-discovered-until-i-deploy-my-app"></a>7. Warum werden meine Tests in UWP-Projekten erst ermittelt, wenn ich meine App bereitstelle?

  UWP-Tests sind auf eine andere Runtime ausgerichtet, wenn die App bereitgestellt wird. Das bedeutet, dass Sie UWP-Projekte nicht nur erstellen, sondern auch bereitstellen müssen, wenn Sie genaue Tests ermitteln möchten.

### <a name="8-how-does-sorting-test-results-work-in-the-hierarchy-view"></a>8. Wie können in der Hierarchieansicht Testergebnisse sortiert werden?

  In der Hierarchieansicht werden Tests alphabetisch und nicht anhand ihrer Ergebnisse sortiert. Über andere Einstellungen zum Sortieren werden Testergebnisse in der Regel erst anhand ihrer Ergebnisse und dann alphabetisch sortiert. Die unterschiedlichen Optionen zum Sortieren sind nachfolgend zum Vergleich dargestellt. Feedback zum Entwurf können Sie [in diesem GitHub-Problem](https://github.com/Microsoft/vstest/issues/1425) geben.

  ![Sortierungsbeispiele](media/testex-sortingex.png)

## <a name="features"></a>Features

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Wie kann ich Featureflags aktivieren, um neue Testfunktionen auszuprobieren?

Featureflags werden verwendet, um experimentelle oder nicht abgeschlossene Teile des Produkts an engagierte Benutzern auszuliefern, die ihr Feedback äußern möchten, bevor die Features offiziell ausgeliefert werden. Sie können Ihre IDE-Erfahrung destabilisieren. Verwenden Sie diese nur in sicheren Entwicklungsumgebungen wie virtuellen Computern. Featureflags sind immer Einstellungen auf eigenes Risiko. Sie können experimentelle Features mit der [Featureflags-Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) oder über die Entwicklereingabeaufforderung aktivieren.

![Featureflags-Erweiterung](media/testex-featureflag.png)

Verwenden Sie zum Aktivieren eines Featureflags über die Visual Studio-Entwicklereingabeaufforderung den folgenden Befehl. Ändern Sie den Pfad zu dem Speicherort, wo Visual Studio auf Ihrem Computer installiert ist, und ändern Sie den Registrierungsschlüssel in das gewünschte Featureflag.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise” HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Sie können das Flag mit dem gleichen Befehl deaktivieren, indem Sie den Wert 0 statt 1 nach dem Dword verwenden.
  
## <a name="see-also"></a>Siehe auch

<xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>  
[Erstellen und Ausführen von Komponententests für vorhandenen Code](http://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
[Komponententest für Code](unit-test-your-code.md)
[Live Unit Testing – häufig gestellte Fragen](live-unit-testing-faq.md)
