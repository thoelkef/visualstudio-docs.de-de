---
title: Visual Studio-Test-Explorer – häufig gestellte Fragen
ms.date: 11/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
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
manager: douge
ms.openlocfilehash: 49df84c5e852cfc282b6d679faf621669cf08148
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296335"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio-Test-Explorer – häufig gestellte Fragen

## <a name="dynamic-test-discovery"></a>Ermitteln dynamischer Tests

**Der Test-Explorer erkennt meine dynamisch definierten Tests nicht. (Z.B. Theorien, benutzerdefinierte Adapter und Merkmale oder „#ifdefs“) Wie kann ich diese Tests ermitteln?**

  Erstellen Sie das Projekt, und vergewissern Sie sich, dass unter **Extras** > **Optionen** > **Test** die assemblybasierte Ermittlung aktiviert ist.

  Bei der [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824) handelt es sich um eine quellenbasierte Testermittlung. Sie kann keine Tests ermitteln, die z.B. Theorien, benutzerdefinierte Adapter und Merkmale oder `#ifdef`-Anweisungen verwenden, da diese zur Laufzeit definiert werden. Ein Build ist erforderlich, damit diese Tests korrekt gefunden werden können. In Visual Studio 2017 Version 15.6 und höher wird die assemblybasierte Ermittlung (die übliche Ermittlung) erst nach Builds ausgeführt. Mit dieser Einstellung wird festgelegt, dass die Testermittlung in Echtzeit während der Bearbeitung so viele Tests wie möglich findet und die assemblybasierte Ermittlung das Anzeigen von dynamisch definierten Tests nach einem Build ermöglicht. Testermittlung in Echtzeit verbessert die Reaktionsfähigkeit, ermöglicht Ihnen aber dennoch, vollständige und genaue Ergebnisse nach einem Build zu erhalten.

## <a name="test-explorer--plus-symbol"></a>Pluszeichen (+) im Test-Explorer

**Was bewirkt das Symbol „+“ (Pluszeichen), das in der obersten Zeile des Test-Explorers angezeigt wird?**

  Das Symbol „+“ (Pluszeichen) gibt an, dass mehr Tests nach einem Build ermittelt werden können, solange die assemblybasierte Ermittlung aktiviert ist. Es wird angezeigt, wenn dynamisch definierte Tests im Projekt erkannt werden.

  ![Plussymbol-Zusammenfassungszeile](media/testex-plussymbol.png)

## <a name="assembly-based-discovery"></a>Assemblybasierte Ermittlung

**Die assemblybasierte Ermittlung funktioniert bei meinem Projekt nicht mehr. Wie kann ich sie wieder aktivieren?**

  Wechseln Sie zu **Extras** > **Optionen** > **Test**, und aktivieren Sie das Kontrollkästchen **Additionally discover tests from built assemblies after builds** (Nach der Builderstellung zusätzliche Tests aus erstellten Assemblys ermitteln).

  ![Assemblybasierte Option](media/testex-toolsoptions.png)

## <a name="real-time-test-discovery"></a>Testermittlung in Echtzeit

**Tests werden jetzt im Test-Explorer angezeigt, während ich schreibe, ohne dass ich mein Projekt erstellen muss. Was hat sich geändert?**

  Dieses Feature wird als [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824) bezeichnet. Dabei wird ein Roslyn-Analysetool verwendet, um Tests zu suchen und den Test-Explorer in Echtzeit aufzufüllen, ohne dass Sie Ihr Projekt erstellen müssen. Weitere Informationen zum Verhalten der Testermittlung bei dynamisch definierten Tests wie Theorien oder benutzerdefinierten Merkmalen finden Sie in der Antwort zur ersten häufig gestellten Frage (FAQ #1).

## <a name="real-time-test-discovery-compatibility"></a>Konformität der Testermittlung in Echtzeit

**In welchen Sprachen und Testframeworks kann die Testermittlung in Echtzeit verwendet werden?**

  Die [Testermittlung in Echtzeit](https://go.microsoft.com/fwlink/?linkid=862824) funktioniert nur für die verwalteten Sprachen (C# und Visual Basic), da sie mit dem Roslyn-Compiler erstellt wird. Derzeit funktioniert Testermittlung in Echtzeit nur für xUnit-, NUnit- und MSTest-Framework.

## <a name="test-explorer-logs"></a>Test-Explorer-Protokolle

**Wie kann ich die Protokollierung für den Test-Explorer aktivieren?**

  Navigieren Sie zu **Extras** > **Optionen** > **Test**, und suchen Sie dort nach dem Protokollbereich.

## <a name="uwp-test-discovery"></a>UWP-Testermittlung

**Warum werden meine Tests in UWP-Projekten erst ermittelt, wenn ich meine App bereitstelle?**

  UWP-Tests sind auf eine andere Runtime ausgerichtet, wenn die App bereitgestellt wird. Das bedeutet, dass Sie UWP-Projekte nicht nur erstellen, sondern auch bereitstellen müssen, wenn Sie genaue Tests suchen möchten.

## <a name="test-explorer-sorting"></a>Sortierung im Test-Explorer

**Wie können in der Hierarchieansicht Testergebnisse sortiert werden?**

  In der Hierarchieansicht werden Tests alphabetisch und nicht anhand ihrer Ergebnisse sortiert. Über andere Einstellungen zum Sortieren werden Testergebnisse in der Regel erst anhand ihrer Ergebnisse und dann alphabetisch sortiert. Beachten Sie zum Vergleich die unterschiedlichen „Gruppieren nach“-Optionen in der folgenden Abbildung. Feedback zum Entwurf können Sie [in diesem GitHub-Problem](https://github.com/Microsoft/vstest/issues/1425) geben.

  ![Sortierungsbeispiele](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Hierarchieansicht des Test-Explorers

**In der Hierarchieansicht sind die Projekt-, Namespace- und Klasse-Gruppierung mit Symbolen für „erfolgreich“, „fehlerhaft“, „übersprungen“ und „nicht ausgeführt“ versehen. Was bedeuten diese Symbole?**

  Die Symbole neben den Gruppierungen „Projekt“, „Namespace“ und „Klasse“ spiegeln den Status der Tests innerhalb der Gruppierung wider. Siehe folgende Tabelle.

  ![Hierarchiesymbole des Test-Explorers](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Suche nach Dateipfad

**Im Test-Explorer-Suchfeld ist kein Dateipfadfilter mehr vorhanden.**

Der Dateipfadfilter im Suchfeld **Test-Explorer** wurde in Visual Studio 2017 Version 15.7, Preview 3 entfernt. Dieses Feature wurde wenig genutzt, und der Test-Explorer kann Testmethoden durch Ausschluss dieses Features schneller abrufen. Wenn diese Änderung Ihren Entwicklungsablauf unterbricht, teilen Sie uns dies über die [Entwicklercommunity](https://developercommunity.visualstudio.com/) mit.

## <a name="remove-undocumented-interfaces"></a>Entfernen nicht dokumentierter Schnittstellen

**Einige testbezogene APIs sind in Visual Studio 2019 nicht länger enthalten. Was hat sich geändert?**

In Visual Studio 2019 werden einige Testfenster-APIs entfernt, die zuvor als öffentlich markiert waren, aber nie offiziell dokumentiert wurden. Diese wurden als frühe Warnung für die Erweiterungsverwaltung in Visual Studio 2017 als „veraltet“ gekennzeichnet. Nach unserer Erkenntnis wurden diese APIs nur durch sehr wenige Erweiterungen ermittelt und mit einer Abhängigkeit konfiguriert. Dies waren `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken` und `SearchFilterTokenType`. Wenn sich diese Änderung auf Ihre Erweiterung auswirkt, teilen Sie uns dies mit, indem Sie einen Fehler in der [Entwicklercommunity](https://developercommunity.visualstudio.com) melden.

## <a name="test-adapter-nuget-reference"></a>NuGet-Verweis auf Testadapter

**In Visual Studio 2017 Version 15.8 werden meine Tests ermittelt, aber nicht ausgeführt.**

Alle Testprojekte müssen den entsprechenden NuGet-Verweis auf den .NET-Testadapters in ihrer CSPROJ-Datei enthalten. Andernfalls wird die folgende Testausgabe im Projekt angezeigt, wenn die Ermittlung durch eine Testadaptererweiterung nach einem Build gestartet wird oder wenn der Benutzer versucht, die ausgewählten Tests auszuführen:

Das **Testprojekt{} verweist auf keinen NuGet-Adapter für .NET. Die Testermittlung oder -ausführung funktioniert für dieses Projekt möglicherweise nicht. Es wird empfohlen, in jedem .NET-Testprojekt in der Projektmappe auf NuGet-Testadapter zu verweisen.**

Anstelle der Verwendung von Testadaptererweiterungen müssen Projekte NuGet-Pakete für Testadapter verwenden. Diese Anforderung führt zu einer erheblichen Leistungsverbesserung und verursacht weniger Probleme bei der Continuous Integration. Weitere Informationen zur Einstellung der .NET-Testadaptererweiterung finden Sie in den [Anmerkungen zu dieser Version](/visualstudio/releasenotes/vs2017-preview-relnotes#testadapterextension).

> [!NOTE]
> Wenn Sie den NUnit 2-Testadapter verwenden und nicht zum NUnit 3-Testadapter migrieren können, haben Sie die Möglichkeit, dieses neue Ermittlungsverhalten in Visual Studio Version 15.8 unter **Extras** > **Optionen** > **Test** zu deaktivieren.

  ![Test-Explorer-Adapterverhalten unter „Extras > Optionen“](media/testex-adapterbehavior.png)

## <a name="uwp-testcontainer-was-not-found"></a>UWP-TestContainer wurde nicht gefunden

**Meine UWP-Tests werden nicht mehr in Visual Studio 2017 Version 15.7 und höher ausgeführt.**

In aktuellen UWP-Testprojekten wird für die Testplattform eine Buildeigenschaft festgelegt, die eine höhere Leistung bei der Ermittlung von Test-Apps ermöglicht. Wenn Sie über ein UWP-Testprojekt verfügen, das vor Visual Studio Version 15.7 initialisiert wurde, wird möglicherweise der folgende Fehler unter **Ausgabe** > **Tests** angezeigt:

**System.AggregateException: One or more errors occurred. ---> System.InvalidOperationException: The following TestContainer was not found {} at Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider <GetTestContainerAsync>d__61.MoveNext()** (System.AggregateException: Mindestens ein Fehler ist aufgetreten. ---> System.InvalidOperationException: Der folgende TestContainer wurde nicht {} in d__61.MoveNext() innerhalb von Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider gefunden.)
  
So beheben Sie diesen Fehler

- Aktualisieren Sie die Buildeigenschaft Ihres Testprojekts mit dem folgenden Code:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aktualisieren Sie die Version des TestPlatform SDK mit dem folgenden Code:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Verwenden von Featureflags

**Wie kann ich Featureflags aktivieren, um neue Testfunktionen auszuprobieren?**

Featureflags werden verwendet, um experimentelle oder nicht abgeschlossene Teile des Produkts an engagierte Benutzern auszuliefern, die ihr Feedback äußern möchten, bevor die Features offiziell ausgeliefert werden. Sie können Ihre IDE-Erfahrung destabilisieren. Verwenden Sie diese nur in sicheren Entwicklungsumgebungen wie virtuellen Computern. Featureflags sind immer Einstellungen auf eigenes Risiko. Sie können experimentelle Features mit der [Featureflags-Erweiterung](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension) oder über die Entwicklereingabeaufforderung aktivieren.

![Featureflags-Erweiterung](media/testex-featureflag.png)

Verwenden Sie zum Aktivieren eines Featureflags über die Visual Studio-Entwicklereingabeaufforderung den folgenden Befehl. Ändern Sie den Pfad zu dem Speicherort, an dem Visual Studio auf Ihrem Computer installiert ist, und ändern Sie den Registrierungsschlüssel in das gewünschte Featureflag.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Sie können das Flag mit dem gleichen Befehl deaktivieren, indem Sie den Wert 0 statt 1 nach dem Dword verwenden.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Create and run unit tests for existing code (Erstellen und Ausführen von Komponententests für verwalteten Code)](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Ausführen von Komponententests für Code](unit-test-your-code.md)
- [Live unit testing FAQ (Live Unit Testing – häufig gestellte Fragen)](live-unit-testing-faq.md)
