---
title: 'DA0030: Sammeln Sie Ebeneninteraktions-Messdaten für Datenbankprojekte. | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26b0905882ef8ec2e3fcddc4cf699ecae7dbe7a4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777475"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Sammeln Sie Ebeneninteraktions-Messdaten für Datenbankprojekte

|||
|-|-|
|Regel-ID|DA0030|
|Kategorie|Verwendung der Profilerstellungstools|
|Profilerstellungsmethode|Stichproben|
|Nachricht|Das Sammeln von Interaktionsmessdaten für Anwendungen mit mehreren Ebenen gibt Aufschluss über Datenbankverwendungsmuster sowie über Verzögerungen beim Zugreifen auf wichtige Daten. Erstellen Sie ein neues Profil für die Anwendung, und aktivieren Sie dabei die Option zum Aktivieren der Profilerstellung für Ebeneninteraktion.|
|Regeltyp|Information|

## <a name="cause"></a>Ursache
 Aufrufe von <xref:System.Data>-Methoden machen einen großen Teil der Profilerstellungsdaten aus, und bei der Profilerstellung wurden keine Ebeneninteraktionsdaten erfasst. Führen Sie eine erneute Profilerstellung aus, und fügen Sie Ebeneninteraktionsdaten hinzu.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird immer dann ausgelöst, wenn bei Funktionen im Namespace „System.Data“ (einschließlich <xref:System.Data.Linq><xref:System.Data.Linq>) umfangreiche Aktivitäten festgestellt werden.

 Bei Anwendungen mit mehreren Ebenen werden für die Präsentations- und Datenebenen Mehrschichtdienste verwendet. Häufig handelt es sich bei der Datenschicht um einen separaten Prozess, von dem ein Datenbankverwaltungssystem wie Microsoft SQL Server ausgeführt wird. Die Datenschicht kann sogar auf einem separaten Computer und damit getrennt vom Rest der Anwendung ausgeführt werden. Samplingprofile geben nur wenig Aufschluss über prozessextern oder remote ausgeführte Funktionen und Dienste.

 Mit den Profilerstellungstools lassen sich Zeitsteuerungsinformationen für Anwendungen mit mehreren Ebenen erfassen, die mittels asynchroner Aufrufe von ADO.NET-Diensten mit einer Microsoft SQL Server-Datenschicht interagieren. Die Profilerstellung für die Ebeneninteraktion muss explizit aktiviert werden. Standardmäßig ist sie deaktiviert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Diese Regel dient nur als Information. Möglicherweise sind keine Korrekturmaßnahmen erforderlich.

 Informationen zum Hinzufügen von Ebeneninteraktionsdaten zu Profilerstellungsdaten mithilfe der Visual Studio-IDE finden Sie unter [Erfassen von Ebeneninteraktionsdaten](../profiling/collecting-tier-interaction-data.md). Informationen zum Hinzufügen von Ebeneninteraktionsdaten zu Profilerstellungsdaten mithilfe der Befehlszeile finden Sie unter [Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile](../profiling/adding-tier-interaction-data-from-the-command-line.md).
