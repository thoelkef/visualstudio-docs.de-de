---
title: PerfTips | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa56b6731e359db486a111194a710069d41a2f1b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295864"
---
# <a name="perftips"></a>PerfTips
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio-Debugger *PerfTips* und die in den Debugger integrierten **Diagnosetools** helfen Ihnen beim Überwachen und Analysieren der Leistung Ihrer App während des Debuggens.  
  
 Obgleich die Debugger-integrierten Diagnosetools eine hervorragende Möglichkeit sind, über Leistungsprobleme während der Entwicklung in Kenntnis gesetzt zu werden, kann der Debugger die Leistung Ihrer App erheblich beeinträchtigen. Zum Erfassen genauerer Leistungsdaten sollten Sie die Visual Studio-Diagnosetools, die auch außerhalb des Debuggers ausgeführt werden können, als zusätzliche Komponente bei Ihren Leistungsuntersuchungen in Erwägung ziehen. See [Run profiling tools without debugging](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
## <a name="perftips"></a>PerfTips  
 Wenn der Debugger die Ausführung an einem Haltepunkt oder während einer schrittweisen Ausführung stoppt, wird die verstrichene Zeit zwischen der Pause und dem vorherigen Haltepunkt als QuickInfo im Editor-Fenster angezeigt. Weitere Informationen finden Sie unter [PerfTips: Performance Information at-a-glance while Debugging with Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Fenster "Diagnosetools"  
 Haltepunkte und die zugehörigen Zeitsteuerungsdaten werden im Fenster Diagnosetools aufgezeichnet.  
  
 Folgende Abbildung zeigt das Fenster „Diagnosetools“ in Visual Studio 2015 Update 1:  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
- Die **Haltepunkt** -Zeitachse kennzeichnet die Haltepunkte, die während der Debugsitzung ermittelt wurden. Klicken Sie auf ein Ereignis, um die **Debugger** -Detailliste auszuwählen.  
  
- Das Diagramm **CPU-Auslastung** zeigt die Änderung in der CPU übergreifend über alle Prozessorkerne in der Debugsitzung an.  
  
- Die Liste **Ereignisse** des **Debugger** -Detailbereichs enthält Elemente für jeden Haltepunkt.  
  
- Die Spalte **Dauer** eines Haltepunkt-Ereignisses zeigt die verstrichene Zeit zwischen Ereignis und dem vorherigen Haltepunkt an.  
  
## <a name="turn-perftips-on-or-off"></a>Aktivieren oder Deaktivieren von PerfTips  
 So aktivieren oder deaktivieren Sie PerfTips:  
  
1. Wählen Sie im Menü **Debuggen** den Befehl **Optionen**aus.  
  
2. Markieren Sie **PerfTip für verstrichene Zeit beim Debuggen anzeigen**oder heben Sie die Auswahl auf.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Aktivieren oder deaktivieren Sie das Fenster „Diagnosetools“  
 Zum Aktivieren oder deaktivieren das Fenster „Diagnosetools“:  
  
1. Wählen Sie im Menü **Debuggen** den Befehl **Optionen**aus.  
  
2. Aktivieren oder deaktivieren Sie **Aktivieren der Diagnosetools während des Debuggens**.
