---
title: 'Vorgehensweise: Festlegen ein Threadnamens in nativem Code | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/17/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 9226e009936d0a644a5a6fcfcaba57bc3af25d7d
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803097"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Vorgehensweise: Festlegen eines Threadnamens in nativem Code
Das Benennen von Threads ist in allen Editionen von Visual Studio möglich. Das Benennen von Threads ist hilfreich beim Verfolgen von Threads im Fenster **Threads**.

## <a name="set-a-thread-name"></a>Festlegen eines Threadnamens

Die `SetThreadName` Funktion ist nützlich zum Festlegen und Anzeigen von Threads, wenn der Debugger an der ausgeführte Code angefügt ist. Ab Visual Studio 2017 Version 15.6, können Sie die [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) Funktion zum Festlegen und Threadnamen anzeigen.

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

## <a name="set-a-thread-name-using-setthreadname"></a>Festlegen eines Threadnamens SetThreadName verwenden

Sie können auch verwenden, um das Festlegen eines Threadnamens im Programm, das `SetThreadName` Funktion, wie im folgenden Codebeispiel gezeigt. Der Threadname wird in den Thread kopiert, damit der Arbeitsspeicher für den `threadName` -Parameter freigegeben werden kann.  Diese Methode verwendet einen auf Ausnahmen basierende Ansatz, der funktioniert nur, wenn zum Zeitpunkt, die die Ausnahmen basierende Methode verwendet wird, der Debugger angefügt ist. Ein Threadnamen, den Sie festlegen, mit dieser Methode wird in Dumps oder Tools zur Leistungsanalyse nicht verfügbar.

Im folgenden Codebeispiel wird veranschaulicht, wie Sie mit `SetThreadName`:

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
 [Vorgehensweise: Festlegen eines Threadnamens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md)