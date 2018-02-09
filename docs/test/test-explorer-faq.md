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
ms.openlocfilehash: db3cf85576e6c46aca14897f7244cd0f56d8d5c2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio-Test-Explorer – häufig gestellte Fragen

## <a name="test-discovery"></a>Testermittlung

### <a name="1-the-test-explorer-is-not-discovering-my-tests-that-have-theories-custom-adapters-custom-traits-use-ifdefs-or-are-dynamically-defined-how-can-i-discover-these-tests"></a>1. Der Test-Explorer ermittelt meine Tests nicht, wenn sie Theorien, benutzerdefinierte Adapter und benutzerdefinierte Merkmale enthalten, #ifdefs verwenden oder dynamisch definiert sind. Wie kann ich diese Tests ermitteln?

  Erstellen Sie das Projekt, und vergewissern Sie sich, dass in **Extras > Optionen > Test** die assemblybasierte Ermittlung aktiviert ist.

  [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824), die quellenbasierte Testermittlung, kann keine Tests ermitteln, die Theorien, benutzerdefinierte Adapter, benutzerdefinierte Merkmale und `#ifdef`-Anweisungen verwenden oder auf andere Weise dynamisch definiert werden. Ein Build ist erforderlich, damit diese Tests korrekt ermittelt werden. In den 15.6-Vorschauen wird die assemblybasierte Ermittlung (die herkömmliche Ermittlung) nur nach Builds ausgeführt. Dies bedeutet, dass Testermittlung in Echtzeit während Ihrer Bearbeitung so viele Tests wie möglich ermittelt, und die assemblybasierte Ermittlung Theorien (oder sonstige dynamisch definierte Tests) nach einem Build ermöglicht. Testermittlung in Echtzeit verbessert die Reaktionsfähigkeit, ermöglicht Ihnen aber dennoch, vollständige und genaue Ergebnisse nach einem Build zu erhalten.

### <a name="2-what-does-the--plus-symbol-that-appears-in-the-top-line-of-test-explorer-mean"></a>2. Was bewirkt das Symbol „+“ (Pluszeichen), das in der obersten Zeile des Test-Explorers angezeigt wird?

  Das Symbol „+“ (Pluszeichen) gibt an, dass mehr Tests nach einem Build ermittelt werden können, wenn die assemblybasierte Ermittlung aktiviert ist. Es wird angezeigt, wenn dynamisch definierte Tests im Projekt erkannt werden.

  ![Plussymbol-Zusammenfassungszeile](media/testex-plussymbol.png)

### <a name="3-assembly-based-discovery-is-no-longer-working-for-my-project-how-do-i-turn-it-back-on"></a>3. Assemblybasierte Ermittlung funktioniert bei meinem Projekt nicht mehr. Wie kann ich sie wieder aktivieren?

  Wechseln Sie zu **Extras > Optionen > Test**, und aktivieren Sie das Kontrollkästchen **Zusätzlich Tests ermitteln, die nach Builds aus Assemblys erstellt wurden.**

  ![Assemblybasierte Option](media/testex-toolsoptions.png)

### <a name="4-tests-now-appear-in-test-explorer-while-i-type-without-having-to-build-my-project-what-changed"></a>4. Tests werden jetzt im Test-Explorer angezeigt, während ich schreibe, ohne dass ich mein Projekt erstellen muss. Was hat sich geändert?

  Dieses Feature wird als [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824) bezeichnet. Dabei wird ein Roslyn-Analysetool verwendet, um Tests zu ermitteln und den Test-Explorer in Echtzeit zu füllen, ohne dass Sie Ihr Projekt erstellen müssen. Weitere Informationen zum Verhalten der Testermittlung bei dynamisch definierten Tests wie Theorien oder benutzerdefinierten Merkmalen finden Sie in der Antwort zur ersten häufig gestellten Frage.

### <a name="5-what-languages-and-test-frameworks-can-use-real-time-test-discovery"></a>5. Welche Sprachen und Testframeworks kann die Testermittlung in Echtzeit verwenden?

  [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824) funktioniert nur für die verwalteten Sprachen (C# und Visual Basic), da sie mit dem Roslyn-Compiler erstellt wird. Derzeit funktioniert Testermittlung in Echtzeit nur für xUnit-, NUnit- und MSTest-Framework.

## <a name="features"></a>Features

### <a name="how-can-i-turn-on-feature-flags-to-try-out-new-testing-features"></a>Wie kann ich Featureflags aktivieren, um neue Testfunktionen auszuprobieren?

Featureflags werden verwendet, um experimentelle oder nicht abgeschlossene Teile des Produkts an engagierte Benutzern auszuliefern, die ihr Feedback äußern möchten, bevor die Features offiziell ausgeliefert werden. Sie können Ihre IDE-Erfahrung destabilisieren. Sie sollten sie nur in sicheren Entwicklungsumgebungen wie virtuellen Computern verwenden. Featureflags sind immer Einstellungen auf eigenes Risiko. Sie können experimentelle Features mit der [Featureflags-Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) oder über die Entwicklereingabeaufforderung aktivieren.

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
