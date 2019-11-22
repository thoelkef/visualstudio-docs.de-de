---
title: 'Vorgehensweise: Festlegen eines Thread namens in nativem Code | Microsoft-Dokumentation'
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
ms.openlocfilehash: 1e719563c831c50cc325d70d0de431f4be1bf514
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911432"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Gewusst wie: Festlegen eines Threadnamens in systemeigenem Code
Das Benennen von Threads ist in allen Editionen von Visual Studio möglich. Die Thread Benennung eignet sich für die Identifizierung von relevanten Threads im **Thread** Fenster beim Debuggen eines laufenden Prozesses. Erkennungs-und Erkennungs Threads können auch hilfreich sein, wenn Sie das Debuggen von Postmortem per Absturz Abbild Überprüfung durchführen und die Leistungs Erfassung mithilfe verschiedener Tools analysieren.

## <a name="ways-to-set-a-thread-name"></a>Möglichkeiten zum Festlegen eines Thread namens

Es gibt zwei Möglichkeiten, einen Thread Namen festzulegen. Der erste erfolgt über die Funktion [setthreaddescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) . Die zweite besteht darin, eine bestimmte Ausnahme auszulösen, während der Visual Studio-Debugger an den Prozess angefügt wird. Jeder Ansatz hat Vorteile und Einschränkungen. Die Verwendung von `SetThreadDescription` wird ab Windows 10, Version 1607 oder Windows Server 2016 unterstützt.

Beachten Sie, dass _beide_ Ansätze zusammen verwendet werden können, wenn gewünscht, da die Mechanismen, mit denen Sie arbeiten, voneinander unabhängig sind.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Legen Sie mit `SetThreadDescription` einen Thread Namen fest.

Vorteile:
* Thread Namen sind beim Debuggen in Visual Studio sichtbar, unabhängig davon, ob der Debugger an den Prozess angefügt wurde, während setthreaddescription aufgerufen wird.
* Thread Namen sind beim Ausführen des Debuggens von Postmortem durch das Laden eines Absturz Abbilds in Visual Studio sichtbar.
* Thread Namen werden auch angezeigt, wenn Sie andere Tools verwenden, z. b. den [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools) -Debugger und [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) Performance Analyzer.

Zu beachten:
* Thread Namen werden nur in Visual Studio 2017, Version 15,6 und höheren Versionen, angezeigt.
* Beim Debuggen einer Absturz Abbild Datei durch das Postmortem-Element werden Thread Namen nur angezeigt, wenn der Absturz unter Windows 10, Version 1607, Windows Server 2016 oder höheren Versionen von Windows erstellt wurde.

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Festlegen eines Thread namens durch Auslösen einer Ausnahme

Eine andere Möglichkeit, einen Thread Namen in Ihrem Programm festzulegen, besteht darin, den gewünschten Thread Namen mit dem Visual Studio-Debugger zu kommunizieren, indem eine speziell konfigurierte Ausnahme ausgelöst wird.

Vorteile:
* Funktioniert in allen Versionen von Visual Studio.

Zu beachten:
* Funktioniert nur, wenn der Debugger zum Zeitpunkt der Verwendung der Ausnahme basierten Methode angefügt wird.
* Thread Namen, die mit dieser Methode festgelegt werden, sind in Abbilder oder Leistungsanalyse Tools nicht verfügbar.

*Beispiel:*

Die `SetThreadName` Funktion, die unten gezeigt wird, veranschaulicht diesen Ausnahme basierten Ansatz. Beachten Sie, dass der Thread Name automatisch in den Thread kopiert wird, damit der Arbeitsspeicher für den `threadName`-Parameter freigegeben werden kann, nachdem der `SetThreadName`-Befehl abgeschlossen wurde.

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
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
- [Gewusst wie: Festlegen eines Threadnamens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md)
