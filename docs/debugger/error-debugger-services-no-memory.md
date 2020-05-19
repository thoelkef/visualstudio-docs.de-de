---
title: Debugdienste verfügen nicht über genügend Arbeitsspeicher | Microsoft-Dokumentation
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
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737839"
---
# <a name="debugger-services-running-out-of-memory"></a>Debuggerdienste verfügen nicht über genügend Arbeitsspeicher
Die Debugdienste verfügen nicht über genügend Arbeitsspeicher, weshalb die Debugsitzung beendet wurde.

## <a name="to-investigate-this-error-on-windows"></a>Untersuchen dieses Fehlers unter Windows
- Sie können das Arbeitsspeicherdiagramm im Fenster **Diagnosetools** überprüfen, um herauszufinden, ob für die Zielanwendung ein deutlich zunehmendes Speichervolumen benötigt wird. Wenn dies der Fall ist, verwenden Sie das Tool **Speicherauslastung**, um das zugrunde liegende Problem zu diagnostizieren (siehe [Messen der Speicherauslastung in Visual Studio](../profiling/memory-usage.md)).

- Wenn die Zielanwendung nicht viel Arbeitsspeicher beansprucht, verwenden Sie das Fenster **Task-Manager**, um die Speicherauslastung von Visual Studio (devenv.exe), des Workerprozesses (msvsmon.exe) oder von VS Code (vsdbg.exe/vsdbg-ui.exe) zu prüfen, um festzustellen, ob es sich um ein Debuggerproblem handelt. Wenn es sich bei dem Prozess, der nicht über genügend Arbeitsspeicher verfügt, um „devenv.exe“ handelt, sollten Sie die Anzahl der ausgeführten Visual Studio-Erweiterungen verringern.

## <a name="see-also"></a>Siehe auch
- [Blogbeitrag: Analyze CPU and Memory while Debugging (Analysieren der CPU und des Arbeitsspeichers beim Debuggen)](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Informationen zur Speicherverwaltung](/windows/win32/memory/about-memory-management)
