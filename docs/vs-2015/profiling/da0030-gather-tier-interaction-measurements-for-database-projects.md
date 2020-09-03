---
title: 'DA0030: Sammeln Sie Ebeneninteraktions-Messdaten für Datenbankprojekte. | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a4b140c1859d3a3a17eb2f48eb02a60a3e9d50c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152628"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Sammeln Sie Ebeneninteraktions-Messdaten für Datenbankprojekte.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-ID | DA0030 |  
| Kategorie | Profilerstellungstools Verwendung |  
| Profil Erstellungs Methode | Stichprobenentnahme |  
| Meldung | Durch das Sammeln von Interaktions Messungen für Anwendungen mit mehreren Stufen können Sie Daten Bank Verwendungs Muster und Verzögerungen beim Zugriff auf wichtige Daten besser verstehen. Erstellen Sie ein neues Profil für die Anwendung, und aktivieren Sie dabei die Option zum Aktivieren der Profilerstellung für Ebeneninteraktion.|  
| Regeltyp | Informationen |  
  
## <a name="cause"></a>Ursache  
 Aufrufe von <xref:System.Data>-Methoden machen einen großen Teil der Profilerstellungsdaten aus, und bei der Profilerstellung wurden keine Ebeneninteraktionsdaten erfasst. Führen Sie eine erneute Profilerstellung aus, und fügen Sie Ebeneninteraktionsdaten hinzu.  
  
## <a name="rule-description"></a>Beschreibung der Regel  
 Diese Regel wird immer dann ausgelöst, wenn bei Funktionen im Namespace „System.Data“ (einschließlich <xref:System.Data.Linq><xref:System.Data.Linq>) umfangreiche Aktivitäten festgestellt werden.  
  
 Bei Anwendungen mit mehreren Ebenen werden für die Präsentations- und Datenebenen Mehrschichtdienste verwendet. Häufig handelt es sich bei der Datenschicht um einen separaten Prozess, von dem ein Datenbankverwaltungssystem wie Microsoft SQL Server ausgeführt wird. Die Datenschicht kann sogar auf einem separaten Computer und damit getrennt vom Rest der Anwendung ausgeführt werden. Samplingprofile geben nur wenig Aufschluss über prozessextern oder remote ausgeführte Funktionen und Dienste.  
  
 Mit den Profilerstellungstools lassen sich Zeitsteuerungsinformationen für Anwendungen mit mehreren Ebenen erfassen, die mittels asynchroner Aufrufe von ADO.NET-Diensten mit einer Microsoft SQL Server-Datenschicht interagieren. Die Profilerstellung für die Ebeneninteraktion muss explizit aktiviert werden. Standardmäßig ist sie deaktiviert.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Diese Regel dient nur als Information. Möglicherweise sind keine Korrekturmaßnahmen erforderlich.  
  
 Informationen zum Hinzufügen von Ebeneninteraktionsdaten zu Profilerstellungsdaten mithilfe der Visual Studio-IDE finden Sie unter [Collecting tier interaction data (Erfassen von Ebeneninteraktionsdaten mit der Visual Studio-IDE)](../profiling/collecting-tier-interaction-data.md). Informationen zum Hinzufügen von Ebeneninteraktionsdaten zu Profilerstellungsdaten mithilfe der Befehlszeile finden Sie unter [Adding tier interaction data from the command line (Hinzufügen von Ebeneninteraktionsdaten über die Befehlszeile)](../profiling/adding-tier-interaction-data-from-the-command-line.md).
