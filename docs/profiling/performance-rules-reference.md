---
title: Referenz zu den Leistungsregeln | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5280226aaba40de42052d72e58928a53af53f631
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543636"
---
# <a name="performance-rules-reference"></a>Referenz zu den Leistungsregeln
Die Leistungsregeln der Profilerstellungstools bieten zusätzliche Warnungen und Informationen über die Leistung Ihrer Anwendung. Leistungsregeln analysieren Daten in einer Profilerstellung, die aus Quellen wie z.B. Windows und Prozessor-Leistungsindikatoren gesammelt werden. Regelnachrichten werden im Fenster Fehlerausgabe der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-IDE angezeigt. Nachrichten werden mit einer der folgenden Regelebenen aufgeführt:

|Kategorie|Beschreibung|
|-|-|
|**Fehler**|Nur wenige Regeln generieren Fehlermeldungen, da die meisten Leistungsprobleme keine tatsächlichen Fehler sind. Eine Fehlermeldung kann einen Fehler beim Erfassen von Profilerstellungsdaten angeben.|
|**Warnung**|Warnungen geben einen Bereich Ihrer Anwendung an, die eine Ursache von Leistungsproblemen sein oder die von Optimierungen profitieren können.|
|**Information**|Informationsnachrichten geben entweder die Analyse einer Regelbedingung an, die den Schwellenwert zur Erstellung einer Fehlermeldung nicht erreicht hat, oder dass die Information in der Nachricht nützlich ist, jedoch nicht auf ein Leistungsproblem hinweist.|

## <a name="in-this-section"></a>In diesem Abschnitt

[Leistungsregeln nach ID](../profiling/performance-rules-by-id.md)

Die Leistungsregeln der Profilerstellungstools sind in vier Kategorien unterteilt:

|Kategorie|Beschreibung|
|-|-|
|[Leistungsregeln für die .NET Framework-Verwendung](../profiling/dotnet-framework-usage-performance-rules.md)|Regeln, mit denen Sie .NET Framework effizient verwenden können.|
|[Leistungsregeln für Speicher und Auslagerung](../profiling/memory-and-paging-performance-rules.md)|Regeln, die den verwalteten Arbeitsspeicher und das Pagingverhalten Ihrer Anwendung analysieren.|
|[Verwendungsregeln für Profilerstellungstools](../profiling/profiling-tools-usage-rules.md)|Regeln, mit denen Sie Profilerstellungstools effizient verwenden können.|
|[Leistungsregeln für die Ressourcenüberwachung](../profiling/resource-monitoring-performance-rules.md)|Informationsnachrichten zur Auslastung von Prozessor und Arbeitsspeicher in einer Profilerstellung.|
