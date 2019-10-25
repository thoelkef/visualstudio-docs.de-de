---
title: Nicht genügend Arbeitsspeicher für Debugger-Dienste | Microsoft-Dokumentation
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
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737839"
---
# <a name="debugger-services-running-out-of-memory"></a>Debuggerdienste verfügen nicht über genügend Arbeitsspeicher
Die debuggingdienste haben nicht genügend Arbeitsspeicher, und die Debuggingsitzung wurde beendet.

## <a name="to-investigate-this-error-on-windows"></a>So untersuchen Sie diesen Fehler unter Windows
- Sie können im Fenster " **Diagnose Tools** " das Prozess Speicher Diagramm überprüfen, um festzustellen, ob die Zielanwendung ein riesiges Wachstum im Arbeitsspeicher aufweist. Wenn dies der Fall ist, verwenden Sie das **Speicher** Auslastungs Tool, um das zugrunde liegende Problem zu diagnostizieren, siehe [Analysieren der Speicherauslastung](../profiling/memory-usage.md).

- Wenn die Zielanwendung nicht viel Arbeitsspeicher beansprucht, verwenden Sie das Fenster **Task-Manager** , um die Speicherauslastung von Visual Studio (devenv. exe), den Arbeitsprozess (msvsmon. exe) oder vs Code (vsdbg. exe/vsdbg-UI. exe) zu prüfen, um festzustellen, ob dies ein Debugger-Problem. Wenn der Prozess, der nicht über genügend Arbeitsspeicher verfügt, devenv. exe ist, sollten Sie die Anzahl der ausgelaufenden Visual Studio-Erweiterungen verringern.

## <a name="see-also"></a>Siehe auch
- [Blog Beitrag: Analysieren der CPU und des Arbeitsspeichers beim Debuggen](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Informationen zur Speicherverwaltung](/windows/win32/memory/about-memory-management)
