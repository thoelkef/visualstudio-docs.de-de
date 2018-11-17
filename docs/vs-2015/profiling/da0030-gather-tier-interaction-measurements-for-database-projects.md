---
title: 'DA0030: Sammeln Sie Ebeneninteraktions-Messdaten für Datenbankprojekte. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16d6275074b3cae6b186fe9bb113e32c33e284af
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796752"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Sammeln Sie Ebeneninteraktions-Messdaten für Datenbankprojekte.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-Id | DA0030 |  
| Kategorie | Verwendung der Profilerstellungstools |  
| Profilerstellungsmethode | Erstellen von Stichproben |  
| Nachricht | Sammeln von interaktionsmessdaten für Anwendungen mit mehreren Ebenen greift können Sie sich über datenbankverwendungsmuster sowie Schlüsseldaten Verzögerungen. Versuchen Sie es erneut mit der Profilerstellung für Ebeneninteraktion-Option aktiviert die profilerstellung. |  
| Regeltyp | Informationen |  
  
## <a name="cause"></a>Ursache  
 Aufrufe von <xref:System.Data>-Methoden machen einen großen Teil der Profilerstellungsdaten aus, und bei der Profilerstellung wurden keine Ebeneninteraktionsdaten erfasst. Führen Sie eine erneute Profilerstellung aus, und fügen Sie Ebeneninteraktionsdaten hinzu.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel wird immer dann ausgelöst, wenn bei Funktionen im Namespace „System.Data“ (einschließlich <xref:System.Data.Linq><xref:System.Data.Linq>) umfangreiche Aktivitäten festgestellt werden.  
  
 Bei Anwendungen mit mehreren Ebenen werden für die Präsentations- und Datenebenen Mehrschichtdienste verwendet. Häufig handelt es sich bei der Datenschicht um einen separaten Prozess, von dem ein Datenbankverwaltungssystem wie Microsoft SQL Server ausgeführt wird. Die Datenschicht kann sogar auf einem separaten Computer und damit getrennt vom Rest der Anwendung ausgeführt werden. Samplingprofile geben nur wenig Aufschluss über prozessextern oder remote ausgeführte Funktionen und Dienste.  
  
 Mit den Profilerstellungstools lassen sich Zeitsteuerungsinformationen für Anwendungen mit mehreren Ebenen erfassen, die mittels asynchroner Aufrufe von ADO.NET-Diensten mit einer Microsoft SQL Server-Datenschicht interagieren. Die Profilerstellung für die Ebeneninteraktion muss explizit aktiviert werden. Standardmäßig ist sie deaktiviert.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Diese Regel dient nur als Information. Möglicherweise sind keine Korrekturmaßnahmen erforderlich.  
  
 Informationen zum Hinzufügen von Ebeneninteraktionsdaten zu Profilerstellungsdaten mithilfe der Visual Studio-IDE finden Sie unter [Collecting tier interaction data (Erfassen von Ebeneninteraktionsdaten mit der Visual Studio-IDE)](../profiling/collecting-tier-interaction-data.md). Informationen zum Hinzufügen von Ebeneninteraktionsdaten zu Profilerstellungsdaten mithilfe der Befehlszeile finden Sie unter [Adding tier interaction data from the command line (Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile)](../profiling/adding-tier-interaction-data-from-the-command-line.md).



