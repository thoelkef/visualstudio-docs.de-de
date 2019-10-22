---
title: Warnungen bei der Analyse von verwaltetem Code
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8fbc5bbb596cc7b790ea456b22a24b582e1b609a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622461"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Warnungen bei der Analyse von verwaltetem Code
Das Tool für die Analyse von verwaltetem Code stellt Warnungen über Regelverletzungen in verwalteten Codebibliotheken bereit. Die Warnungen werden in Regelbereichen, etwa Design, Lokalisierung, Leistung und Sicherheit, angeordnet. Jede Warnung steht für die Verletzung einer Analyseregel für verwalteten Code. Dieser Abschnitt enthält ausführliche Diskussionen und Beispiele für jede Warnung zur Analyse von verwaltetem Code.

 Die folgende Tabelle zeigt die Art der Informationen, die für jede Warnung bereitgestellt werden.

|Element|Beschreibung|
|----------|-----------------|
|Geben Sie Folgendes ein:|TypeName für die Regel.|
|CheckId|Eindeutiger Bezeichner für die Regel. CheckId und Category werden für die Unterdrückung einer Warnung im Quellcode verwendet.|
|Kategorie|Kategorie der Warnung.|
|Unterbrechende Änderung|Gibt an, ob die Lösung einer Verletzung der Regel eine unterbrechende Änderung ist. Unterbrechende Änderung bedeutet, dass eine Assembly, die eine Abhängigkeit von dem Ziel aufweist, das die Verletzung verursacht hat, nicht mit der neuen behobenen Version erneut kompiliert wird oder aufgrund der Änderung zur Laufzeit möglicherweise fehlschlägt. Wenn mehrere Korrekturen verfügbar sind und mindestens eine Lösung eine Breaking Change und eine Korrektur nicht besteht, werden sowohl "Breaking" als auch "non-breaking" angegeben.|
|Ursache|Der spezielle verwaltete Code, aufgrund dessen die Regel eine Warnung generiert.|
|Beschreibung|Erläutert die Probleme, die zur Warnung geführt haben.|
|Behandeln von Verstößen|Erläutert, wie der Quellcode geändert werden kann, damit die Regel eingehalten wird und sie keine Warnung mehr generiert.|
|Wann sollten Warnungen unterdrückt werden?|Beschreibt, wann es sicher ist, eine Warnung der Regel zu unterdrücken.|
|Beispielcode|Beispiele, die die Regel verletzen, und korrigierte Beispiele, die die Regel erfüllen.|
|Zugehörige Warnungen|Zugehörige Warnungen.|

## <a name="in-this-section"></a>In diesem Abschnitt

|||
|-|-|
|[Warnungen nach CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Listet alle Warnungen nach CheckId auf|
|[Kryptografiewarnungen](../code-quality/cryptography-warnings.md)|Warnungen, die sicherere Bibliotheken und Anwendungen durch die korrekte Verwendung von Kryptografie unterstützen.|
|[Entwurfswarnungen](../code-quality/design-warnings.md)|Warnungen, die ein korrektes Bibliotheks Design gemäß den .net-Entwurfs Richtlinien unterstützen.|
|[Dokumentations Warnungen](../code-quality/documentation-warnings.md)|Warnungen, die einen gut dokumentierten Bibliotheks Entwurf durch die korrekte Verwendung von XML-Dokumentations Kommentaren unterstützen.|
|[Globalisierungswarnungen](../code-quality/globalization-warnings.md)|Warnungen, die global verwendbare Bibliotheken und Anwendungen unterstützen.|
|[Interoperabilitätswarnungen](../code-quality/interoperability-warnings.md)|Warnungen, die die Interaktion mit COM-Clients unterstützen.|
|[Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md)|Warnungen, die die Bibliotheks- und Anwendungswartung unterstützen.|
|[Mobility Warnings](../code-quality/mobility-warnings.md)|Warnungen, die einen effizienten Stromverbrauch unterstützen.|
|[Benennungswarnungen](../code-quality/naming-warnings.md)|Warnungen, die die Einhaltung der Benennungs Konventionen der .net-Entwurfs Richtlinien unterstützen.|
|[Leistungswarnungen](../code-quality/performance-warnings.md)|Warnungen, die leistungsstarke Bibliotheken und Anwendungen unterstützen.|
|[Portabilitätswarnungen](../code-quality/portability-warnings.md)|Warnungen, die Portabilität auf verschiedenen Plattformen unterstützen.|
|[Zuverlässigkeitswarnungen](../code-quality/reliability-warnings.md)|Warnungen, die Bibliotheks- und Anwendungszuverlässigkeit unterstützen, wie z. B. die richtige Speicher- und Threadverwendung.|
|[Sicherheitswarnungen](../code-quality/security-warnings.md)|Warnungen, die sicherere Bibliotheken und Anwendungen unterstützen.|
|[Verwendungswarnungen](../code-quality/usage-warnings.md)|Warnungen, die die entsprechende Verwendung von .NET unterstützen.|
|[Richtlinienfehler bei der Codeanalyse](../code-quality/code-analysis-policy-errors.md)|Fehler die auftreten, wenn die Codeanalyserichtlinie beim Einchecken nicht erfüllt wird.|
