---
title: Warnungen bei der Analyse von verwaltetem Code
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 77428bfc815a963e8fae4ddae5e5e7a7b7d991fe
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90034103"
---
# <a name="net-code-analysis-rules"></a>.NET-Code Analyse Regeln
Die .NET-Code Analyse enthält Regeln, die auf Code Qualitäts Verletzungen oder Vorschläge zur Verbesserung der Codequalität hinweisen. Die Regeln sind in Regel Bereichen, z. b. Entwurf, Lokalisierung, Leistung und Sicherheit, angeordnet. Bestimmte Regeln gelten speziell für die .NET-API-Verwendung, während die verbleibenden Regeln die generische Codequalität sind. Dieser Abschnitt enthält ausführliche Diskussionen und Beispiele für jede Regel.

 In der folgenden Tabelle werden die Informationen angezeigt, die für die einzelnen Diagnosen bereitgestellt werden.

|Element|BESCHREIBUNG|
|----------|-----------------|
|Typ|TypeName für die Regel.|
|CheckId|Eindeutiger Bezeichner für die Regel. CheckId und Category werden für die Unterdrückung einer Warnung im Quellcode verwendet.|
|Category|Kategorie der Warnung.|
|Unterbrechende Änderung|Gibt an, ob die Lösung einer Verletzung der Regel eine unterbrechende Änderung ist. Unterbrechende Änderung bedeutet, dass eine Assembly, die eine Abhängigkeit von dem Ziel aufweist, das die Verletzung verursacht hat, nicht mit der neuen behobenen Version erneut kompiliert wird oder aufgrund der Änderung zur Laufzeit möglicherweise fehlschlägt. Wenn mehrere Korrekturen verfügbar sind und mindestens eine Lösung eine Breaking Change und eine Korrektur nicht besteht, werden sowohl "Breaking" als auch "non-breaking" angegeben.|
|Ursache|Der spezielle verwaltete Code, aufgrund dessen die Regel eine Warnung generiert.|
|BESCHREIBUNG|Erläutert die Probleme, die zur Warnung geführt haben.|
|Behandeln von Verstößen|Erläutert, wie der Quellcode geändert werden kann, damit die Regel eingehalten wird und sie keine Warnung mehr generiert.|
|Wann sollten Warnungen unterdrückt werden?|Beschreibt, wann es sicher ist, eine Warnung der Regel zu unterdrücken.|
|Beispielcode|Beispiele, die die Regel verletzen, und korrigierte Beispiele, die die Regel erfüllen.|
|Zugehörige Warnungen|Zugehörige Warnungen.|

## <a name="in-this-section"></a>In diesem Abschnitt

|Category|BESCHREIBUNG|
|-|-|
|[Regeln nach ID](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Listet alle Regeln nach RuleId auf.|
|[Entwurfsregeln](../code-quality/design-warnings.md)|Regeln, die ein korrektes Bibliotheks Design gemäß den .net-Entwurfs Richtlinien unterstützen.|
|[Dokumentations Regeln](../code-quality/documentation-warnings.md)|Regeln, die einen gut dokumentierten Bibliotheks Entwurf durch die korrekte Verwendung von XML-Dokumentations Kommentaren unterstützen.|
|[Globalisierungsregeln](../code-quality/globalization-warnings.md)|Regeln, die weltweit einsatzbereite Bibliotheken und Anwendungen unterstützen.|
|[Wartbarkeitsregeln](../code-quality/maintainability-warnings.md)|Regeln, die Bibliotheks-und Anwendungs Wartung unterstützen.|
|[Benennungs Regeln](../code-quality/naming-warnings.md)|Regeln, die die Einhaltung der Benennungs Konventionen der .net-Entwurfs Richtlinien unterstützen.|
|[Leistungs Regeln](../code-quality/performance-warnings.md)|Regeln, die hochleistungsfähige Bibliotheken und Anwendungen unterstützen.|
|[Portabilität und Interoperabilitäts Regeln](../code-quality/interoperability-warnings.md)|Regeln, die Portabilität auf verschiedenen Plattformen und die Interaktion mit com-Clients unterstützen.|
|[Regeln veröffentlichen](../code-quality/publish-warnings.md)|Regeln, die die entsprechende Veröffentlichung von .NET-Anwendungen unterstützen.|
|[Zuverlässigkeitsregeln](../code-quality/reliability-warnings.md)|Regeln, die die Zuverlässigkeit von Bibliotheken und Anwendungen unterstützen, z. b. die korrekte Speicher-und Thread Verwendung|
|[Sicherheitsregeln](../code-quality/security-warnings.md)|Regeln, die sicherere Bibliotheken und Anwendungen unterstützen.|
|[Nutzungsregeln](../code-quality/usage-warnings.md)|Regeln, die die entsprechende Verwendung von .NET unterstützen.|
