---
title: 'Vorgehensweise: Festlegen ein Threadnamens in nativem Code | Microsoft-Dokumentation'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c547dd00f7a5a31b949d22c13f305050355207c7
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227315"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Gewusst wie: Festlegen eines Threadnamens in nativem Code
Das Benennen von Threads ist in allen Editionen von Visual Studio möglich. Benennen von Threads ist nützlich zum Identifizieren von Threads von Interesse an der **Threads** Wartungszeitfensters, in einen laufenden Prozess zu debuggen. Mit Threads in Form Namen kann auch nützlich beim Ausführen der Post-Mortem-debugging über Crash Dumps Untersuchung und beim Analysieren der Leistung werden erfasst, die mit verschiedenen Tools.

## <a name="ways-to-set-a-thread-name"></a>Möglichkeiten zum Festlegen eines Threadnamens

Es gibt zwei Möglichkeiten zum Festlegen eines Threadnamens. Die erste besteht die [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) Funktion. Die zweite ist durch eine bestimmte Ausnahme auslösen, während Visual Studio-Debugger an den Prozess angefügt ist. Jeder Ansatz hat Vorteile und Einschränkungen.

Es ist, beachten Sie, dass _sowohl_ Ansätze können zusammen verwendet werden, bei Bedarf, da die Mechanismen, die mit dem sie arbeiten unabhängig voneinander sind.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Festlegen eines Threadnamens mithilfe von `SetThreadDescription`

Vorteile:
* Threadnamen sind sichtbar, wenn das Debuggen in Visual Studio, unabhängig davon, ob der Debugger an den Prozess zum Zeitpunkt angefügt wurde, der SetThreadDescription aufgerufen wird.
* Threadnamen sind sichtbar, beim Ausführen der Post-Mortem-Debuggen, indem Sie ein Absturzabbild in Visual Studio geladen.
* Threadnamen werden auch angezeigt, wenn andere Tools wie z. B. mithilfe der [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) Debugger und die [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) Leistungsanalyse.

Zu beachten:
* Threadnamen sind nur sichtbar, in Visual Studio 2017 Version 15.6 und höher.
* Beim Debuggen eines Absturzes Post-Mortem-Datei speichern, sind Threadnamen nur sichtbar, wenn der Absturz auf Windows 10, Version 1607, Windows Server 2016 oder höheren Versionen von Windows erstellt wurde.

*Beispiel:*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Festlegen eines Threadnamens durch Auslösen einer Ausnahme

Eine weitere Möglichkeit zum Festlegen eines Threadnamens im Programm ist, um den Namen des gewünschten Thread mit Visual Studio-Debugger zu kommunizieren, durch eine speziell konfigurierte Ausnahme auslösen.

Vorteile:
* Funktioniert in allen Versionen von Visual Studio.

Zu beachten:
* Funktioniert nur, wenn zum Zeitpunkt, die die Ausnahmen basierende Methode verwendet wird, der Debugger angefügt ist.
* Threadnamen, die festlegen, indem Sie mit dieser Methode werden in Dumps oder Tools zur Leistungsanalyse nicht verfügbar sein.

*Beispiel:*

Die `SetThreadName` Funktion, die unten gezeigten veranschaulicht dieses Ausnahme-basierten Ansatzes. Beachten Sie, dass der Threadname automatisch auf den Thread kopiert werden, damit der Speicher für die `threadName` -Parameter freigegeben werden kann, nachdem die `SetThreadName` Aufruf abgeschlossen ist.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>Siehe auch
[Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)  
[Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)  
[Gewusst wie: Festlegen eines Threadnamens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md)
