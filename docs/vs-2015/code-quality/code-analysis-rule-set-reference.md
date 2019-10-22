---
title: Referenz für Code Analyse-Regel Satz | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3c0b347f186c5adee6cf86a0e1720ebfa80f253
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670114"
---
# <a name="code-analysis-rule-set-reference"></a>Codeanalyse-Regelsatzreferenz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie die Code Analyse für Projekte mit verwaltetem Code in [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] oder [!INCLUDE[vsPro](../includes/vspro-md.md)]you konfigurieren, wird eine Liste der integrierten *Regelsätze*angezeigt. Sie können entweder einen der Standardregelsätze verwenden oder einen Regelsatz an Ihre Projektanforderungen anpassen.

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
|[Regelsatz für verwaltete Mindestregeln für verwalteten Code](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|Diese Regeln zielen auf die kritischsten Probleme in Ihrem Code ab, für die die Codeanalyse die genaueste Lösung darstellt.  Es gibt nur wenige dieser Regeln und sie sind nur für die Verwendung in begrenzten Visual Studio-Editionen vorgesehen.  Verwenden Sie MinimumRecommendedRules.ruleset in Verbindung mit anderen Visual Studio-Editionen.|
|[Regelsatz für verwaltete empfohlene Regeln für verwalteten Code](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|Diese Regeln zielen auf die kritischsten Probleme in Ihrem Code ab, einschließlich potenzieller Sicherheitslücken, Anwendungsabstürzen und anderer entscheidender Logik- und Entwurfsfehler. Sie sollten diesen Regelsatz in alle benutzerdefinierten Regelsätze einbinden, die Sie für Ihre Projekte erstellen.|
|[Regelsatz für gemischte Mindestregeln](../code-quality/mixed-minimum-rules-rule-set.md)|Diese Regeln zielen auf die kritischsten Probleme in C++-Projekten mit Common Language Runtime-Unterstützung ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre C++-Projekte mit Common Language Runtime-Unterstützung erstellen.|
|[Regelsatz für gemischte empfohlene Mindestregeln](../code-quality/mixed-recommended-rules-rule-set.md)|Diese Regeln zielen auf die häufigsten und kritischsten Probleme in C++-Projekten mit Common Language Runtime-Unterstützung ab, einschließlich potenzieller Sicherheitslücken, Anwendungsabstürze und anderen wichtigen Logik- und Designfehlern. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre C++-Projekte mit Common Language Runtime-Unterstützung erstellen.  Dieser Regelsatz ist für die Konfiguration mit Visual Studio Professional Edition und höher vorgesehen.|
|[Regelsatz für systemeigene Mindestregeln](../code-quality/native-minimum-rules-rule-set.md)|Diese Regeln zielen auf die kritischsten Probleme in Ihrem nativen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürzen. Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen.|
|[Regelsatz für systemeigene empfohlene Regeln](../code-quality/native-recommended-rules-rule-set.md)|Diese Regeln zielen auf die kritischsten und häufigsten Probleme im systemeigenen Code ab, einschließlich potenzieller Sicherheitslücken und Anwendungsabstürze.  Der Regelsatz sollte in allen benutzerdefinierten Regelsätzen enthalten sein, die Sie für Ihre eigenen Projekte erstellen.  Dieser Regelsatz ist für die Verwendung mit Visual Studio Professional Edition und höher vorgesehen.|
|[Regelsatz für Sicherheitsregeln für verwalteten Code](../code-quality/security-rules-rule-set-for-managed-code.md)|Dieser Regelsatz enthält alle Microsoft-Sicherheitsregeln. Binden Sie diesen Regelsatz mit ein, um die Anzahl gemeldeter potenzieller Sicherheitsprobleme zu maximieren.|
