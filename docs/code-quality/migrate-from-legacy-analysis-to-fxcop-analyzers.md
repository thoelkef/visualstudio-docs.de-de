---
title: Migrieren von FxCop zur Quell Analyse (FxCop-Analyzers)
ms.custom: SEO-VS-2020
description: Erfahren Sie, wie Sie Code zum ersten Mal analysieren oder von FxCop (Binary Analysis) zur neuen Methode der Analyse von verwaltetem Code mithilfe der Quell Analyse (FxCop-Analyzers) migrieren.
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2109d7cbcaaf56600812e27c3055fb3198848228
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810206"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Migration von der Legacy Analyse (FxCop) zur Quell Analyse (FxCop-Analyzers)

Die Quell Analyse durch .NET Compiler Platform ("Roslyn")-Analysen ersetzt die [Legacy Analyse](../code-quality/code-analysis-for-managed-code-overview.md) für verwalteten Code. Bei neueren Projektvorlagen wie .net Core und .NET Standard Projekten ist die Legacy Analyse nicht verfügbar.

Viele der Regeln für die Legacy Analyse (FxCop) wurden bereits für FxCop-Analyzers umgeschrieben, eine Reihe von Roslyn-Code Analysemodulen. Sie [Installieren FxCop-Analysen als ein nuget-Paket](install-fxcop-analyzers.md#nuget-package) , auf das vom Projekt oder der Projekt Mappe verwiesen wird. FxCop-Analysetools führen während der Ausführung des Compilers Analysen aus, die auf dem Quellcode basieren. Die Analyseergebnisse werden zusammen mit den Ergebnissen der Kompilierung gemeldet.

Weitere Informationen zu den Unterschieden zwischen der Legacy-und der Quell Analyse finden Sie in den folgenden Quellen:

- [Quellcodeanalyse im Vergleich zur Legacyanalyse](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers)

- [FAQ zu FxCop-Analyzern](../code-quality/fxcop-analyzers-faq.md)

[Installieren Sie die FxCop](../code-quality/install-fxcop-analyzers.md)-Analysetools, um zur Quell Analyse zu migrieren. Wenn Verstöße bei der Quellcodeanalyse gefunden werden, werden diese ähnlich wie bei der Legacyanalyse im Fenster „Fehlerliste“ in Visual Studio angezeigt. Außerdem erscheinen Verstöße bei der Quellcodeanalyse auch im Code-Editor als *Wellenlinie* unter dem fehlerhaften Code. Die Farbe der Wellenlinie hängt von den [Schweregradeinstellungen](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) der Regel ab. Informationen zum Status der Regeln, die in die neuen FxCop-Analyzers portiert werden, finden Sie unter [portierte und nicht portierte Regeln](../code-quality/fxcop-rule-port-status.md).

Weitere Informationen zum Konfigurieren der FxCop-Analyzers finden Sie unter:

- Informationen zum Konfigurieren von FxCop-Analyzern finden Sie unter [Konfigurieren von FxCop-Analysen](../code-quality/configure-fxcop-analyzers.md).

- Weitere Informationen zum Konfigurieren von Analysemodulen mithilfe von vordefinierten Regeln mit Editor config oder einer Regel Satz Datei finden Sie unter [Aktivieren einer Kategorie von Regeln](../code-quality/analyzer-rule-sets.md).