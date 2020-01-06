---
title: Codeanalyse-Regelsatzreferenz
ms.date: 04/04/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d380346b7e049a6ffc4e8d03a5be27983de10249
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587237"
---
# <a name="code-analysis-rule-set-reference"></a>Codeanalyse-Regelsatzreferenz

Wenn Sie die Legacy-Analyse für Projekte mit verwaltetem Code in Visual Studio konfigurieren, können Sie aus einer Liste integrierter *Regelsätze*auswählen. Einige Regeln sind in mehr als einem der integrierten Regelsätze enthalten, z. b. enthält der Regelsatz "grundlegende Regeln für Richtigkeit" Regeln, die im Regelsatz für verwaltete Empfohlene Regeln enthalten sind.

> [!NOTE]
> Die Regelsätze in diesem Abschnitt beziehen sich auf die Legacy-Analyse. Weitere Informationen zu Regelsätzen, die für Code Analyzer-Pakete verfügbar sind, finden Sie unter [Verwenden von Regelsätzen mit Code Analyse](analyzer-rule-sets.md)Modulen.

Sie können entweder eine der folgenden integrierten Regelsätze verwenden, oder Sie können [Anpassen eines Regelsatzes](../code-quality/how-to-create-a-custom-rule-set.md) an Ihre projektanforderungen anpassen. Wenn Sie mehrere Regelsätze einschließen, die dieselbe Regel in einem benutzerdefinierten Regelsatz enthalten, wird diese Regel nur einmal im benutzerdefinierten Regelsatz angezeigt.

Die Themen in diesem Abschnitt beschreiben die integrierte Regelsätze Mengen und die Regeln (oder Warnungen), die sie enthalten.

| Regelsatz | Enthaltene Regeln |
| - | - |
| [Alle Regeln](all-rules-rule-set.md) | Enthält alle verfügbaren verwalteten C++ und-Regeln |
| [Grundlegende Richtigkeit von Regeln](basic-correctness-rules-rule-set-for-managed-code.md) | Schließt verwaltete Empfohlene Regeln sowie Regeln für Logic Errors und Framework-Verwendung ein. |
| [Erweiterte Regeln für Richtigkeit](extended-correctness-rules-rule-set-for-managed-code.md) | Enthält grundlegende Regeln zur Richtigkeit (einschließlich verwalteter empfohlener Regeln) sowie weitere Regeln für Logikfehler und die frameworkverwendung. |
| [Grundlegende Regeln für Entwurfs Richtlinien](basic-design-guideline-rules-rule-set-for-managed-code.md) | Umfasst verwaltete Empfohlene Regeln und Regeln, mit denen sichergestellt werden kann, dass Code einfach zu lesen, zu verstehen und zu warten |
| [Regeln für erweiterte Entwurfs Richtlinien](extended-design-guidelines-rules-rule-set-for-managed-code.md) | Umfasst grundlegende Regeln für die Entwurfsrichtlinie (einschließlich verwalteter empfohlener Regeln) sowie weitere wart barkeits Regeln, die sich auf die Benennung konzentrieren |
| [Globalisierungsregeln](globalization-rules-rule-set-for-managed-code.md) | Schließt Regeln für Globalisierungs Probleme ein. |
| [Verwaltete Mindestregeln](managed-minimum-rules-rule-set-for-managed-code.md) | Enthält vier Regeln für kritische Probleme mit verwaltetem Code. |
| [Verwaltete Empfohlene Regeln](managed-recommended-rules-rule-set-for-managed-code.md) | Schließt verwaltete Mindestregeln und mehr Regeln für kritische Probleme mit verwaltetem Code ein. |
| [Gemischte Mindestregeln](mixed-minimum-rules-rule-set.md) | Schließt Regeln für kritische Probleme im C++ Code für CLR ein. |
| [Gemischte Empfohlene Regeln](mixed-recommended-rules-rule-set.md) | Schließt gemischte minimal Regeln und mehr Regeln für kritische Probleme im C++ Code für CLR ein. |
| [Systemeigene Mindestregeln](native-minimum-rules-rule-set.md) | Enthält Regeln für kritische Probleme in nativem Code. |
| [Systemeigene Empfohlene Regeln](native-recommended-rules-rule-set.md) | Umfasst systemeigene Mindestregeln und mehr Regeln für kritische Probleme in System eigenem Code |
| [Sicherheitsregeln](security-rules-rule-set-for-managed-code.md) | Enthält Regeln zum Ermitteln von Sicherheitsrisiken. |
