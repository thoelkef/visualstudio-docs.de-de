---
title: Code Analysis-regelsatzreferenz | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0bc2b01641c6f6b333ef5323a60672818cc5e7b3
ms.sourcegitcommit: bfa26fd7426af0d065cb2eef3d6827b5d6f7986c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2018
---
# <a name="code-analysis-rule-set-reference"></a>Codeanalyse-Regelsatzreferenz

Wenn Sie die Codeanalyse für Projekte mit verwaltetem Code in Visual Studio konfigurieren, Clientanzahl eine Liste mit integrierten *-Regelsätze*. Sie können entweder einen der Standardregelsätze verwenden oder Sie können einen Regelsatz an Ihre projektanforderungen anpassen anpassen.

## <a name="available-rule-sets"></a>Verfügbare Regelsätze

In der folgenden Tabelle sind die Standardregelsätze aufgeführt:

|||
|-|-|
|[Regelsatz für alle Regeln](../code-quality/all-rules-rule-set.md)|Dieser Regelsatz enthält alle Regeln. Das Ausführen dieses Regelsatzes führt möglicherweise zu einer hohen Anzahl gemeldeter Warnungen. Verwenden Sie diesen Regelsatz, um einen Überblick über alle Probleme in Ihrem Code zu erhalten. Dies kann Ihnen bei der Entscheidung behilflich sein, welche der spezifischeren Regelsätze für Ihre Projekte am besten geeignet sind.|
|[Regelsatz für die grundlegenden Regeln für Richtigkeit für verwalteten Code](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|Diese Regeln zielen auf logische Fehler und häufige Irrtümer bei der Verwendung von Framework-APIs ab. Binden Sie diesen Regelsatz zur Erweiterung der Liste von Warnungen mit ein, die von den empfohlenen Mindestregeln gemeldet werden.|
|[Regelsatz für die einfachen Entwurfsrichtlinienregeln für verwalteten Code](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|Diese Regeln zielen auf die Erzwingung von Best Practices ab, sodass Ihr Code leicht verständlich und einfach zu verwenden ist. Binden Sie diesen Regelsatz mit ein, wenn Ihr Projekt Bibliothekscode umfasst oder wenn Sie Best Practices erzwingen möchten, um einen leicht verwaltbaren Code zu gewährleisten.|
|[Regelsatz für die erweiterten Regeln für Richtigkeit für verwalteten Code](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|Diese Regeln erweitern die grundlegenden Regeln für Richtigkeit und maximieren die gemeldeten Fehler bezüglich Logik und Frameworkverwendung. Besonderes Augenmerk wird auf spezifische Szenarien gelegt, z. B. COM-Interop und mobile Anwendungen. Binden Sie diesen Regelsatz mit ein, wenn eines dieser Szenarien auf Ihr Projekt zutrifft, oder um weitere Probleme in Ihrem Projekt zu ermitteln.|
|[Regelsatz für die erweiterten Entwurfsrichtlinienregeln für verwalteten Code](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|Diese Regeln erweitern die grundlegenden Regeln für Entwurfsrichtlinien und maximieren die gemeldeten Fehler bezüglich Verwendbarkeit und Wartbarkeit. Besonderes Augenmerk wird auf Benennungsrichtlinien gelegt. Binden Sie diesen Regelsatz mit ein, wenn Ihr Projekt Bibliothekscode umfasst, oder wenn Sie höchste Standards für das Schreiben von verwaltbarem Code erzwingen möchten.|
|[Regelsatz für Globalisierungsregeln für verwalteten Code](../code-quality/globalization-rules-rule-set-for-managed-code.md)|Diese Regeln zielen auf Probleme ab, durch die verhindert wird, dass Daten in Ihrer Anwendung bei Verwendung in unterschiedlichen Sprachen, Gebietsschemas und Kulturen ordnungsgemäß angezeigt werden. Binden Sie diesen Regelsatz mit ein, wenn Ihre Anwendung lokalisiert oder globalisiert wird.|
|[Verwaltete Mindestregeln-Regelsatz für verwalteten code](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Diese Regeln zielen auf die kritischsten Probleme in Ihrem Code ab, für die die Codeanalyse die genaueste Lösung darstellt. Es gibt nur wenige dieser Regeln und sie sind nur für die Verwendung in begrenzten Visual Studio-Editionen vorgesehen. Verwenden Sie MinimumRecommendedRules.ruleset in Verbindung mit anderen Visual Studio-Editionen.|
|[Regelsatz für verwaltete empfohlene Regeln für verwalteten Code](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Diese Regeln zielen auf die kritischsten Probleme in Ihrem Code ab, einschließlich potenzieller Sicherheitslücken, Anwendungsabstürzen und anderer entscheidender Logik- und Entwurfsfehler. Sie sollten diesen Regelsatz in alle benutzerdefinierten Regelsätze einbinden, die Sie für Ihre Projekte erstellen.|
|[Regelsatz für gemischte Mindestregeln](../code-quality/mixed-minimum-rules-rule-set.md)|Diese Regeln zielen auf die kritischsten Probleme in C++-Projekten mit Common Language Runtime-Unterstützung ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre C++-Projekte mit Common Language Runtime-Unterstützung erstellen.|
|[Regelsatz für gemischte empfohlene Mindestregeln](../code-quality/mixed-recommended-rules-rule-set.md)|Diese Regeln zielen auf die häufigsten und kritischsten Probleme in C++-Projekten mit Common Language Runtime-Unterstützung ab, einschließlich potenzieller Sicherheitslücken, Anwendungsabstürze und anderen wichtigen Logik- und Designfehlern. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre C++-Projekte mit Common Language Runtime-Unterstützung erstellen. |
|[Regelsatz für systemeigene Mindestregeln](../code-quality/native-minimum-rules-rule-set.md)|Diese Regeln zielen auf die kritischsten Probleme in Ihrem nativen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen.|
|[Regelsatz für systemeigene empfohlene Regeln](../code-quality/native-recommended-rules-rule-set.md)|Diese Regeln zielen auf die kritischsten und häufigsten Probleme im nativen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürze. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen. |
|[Regelsatz für Sicherheitsregeln für verwalteten Code](../code-quality/security-rules-rule-set-for-managed-code.md)|Dieser Regelsatz enthält alle Microsoft-Sicherheitsregeln. Binden Sie diesen Regelsatz mit ein, um die Anzahl gemeldeter potenzieller Sicherheitsprobleme zu maximieren.|
