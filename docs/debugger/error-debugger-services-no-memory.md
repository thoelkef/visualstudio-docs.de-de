---
title: Debugger-Dienste, die nicht genügend Arbeitsspeicher ausgeführt werden. | Microsoft-Dokumentation
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "67854017"
---
# <a name="debugger-services-running-out-of-memory"></a>Debugger-Dienste, die nicht genügend Arbeitsspeicher ausgeführt werden.
Das Debuggen von Webdiensten nicht genügend Arbeitsspeicher und das Beenden der Debugsitzung verursacht.

## <a name="to-investigate-this-error-on-windows"></a>Um diesen Fehler auf Windows zu untersuchen.
- Sehen Sie sich das arbeitsspeicherdiagramm Prozess der **Diagnosetools** Fenster aus, um festzustellen, ob die Anwendung große Vergrößerung im Arbeitsspeicher auftreten. Wenn dies der Fall ist, verwenden Sie die **Speicherauslastung** Tool zum Diagnostizieren von Was ist das zugrunde liegende Problem, finden Sie unter [Analysieren der speicherauslastung](../profiling/memory-usage.md).

- Wenn die Zielanwendung nicht anscheinend viel Arbeitsspeicher beansprucht werden, verwenden Sie die **Task-Manager** Fenster aus, um die speicherauslastung von Visual Studio (devenv.exe), den Arbeitsprozess (msvsmon.exe), oder der Visual Studio Code (vsdbg.exe/vsdbg-ui.exe) zum Auschecken Bestimmt, ob dies ein Problem der Debugger ist. Ist der Prozess ausgeführt wird, nicht genügend Arbeitsspeicher devenv.exe, reduzieren Sie die Anzahl von Visual Studio-Erweiterungen, die ausgeführt wird.

## <a name="see-also"></a>Siehe auch
- [Blogbeitrag: Analysieren von CPU und Arbeitsspeicher während des Debuggens](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Zur Verwaltung des Arbeitsspeichers](/windows/win32/memory/about-memory-management)
