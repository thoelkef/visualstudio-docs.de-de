---
title: Zuordnungs-Hook-Funktionen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f684c6c66448fdab2ee7607a81ff7ed769a5e607
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745819"
---
# <a name="allocation-hook-functions"></a>Hookfunktionen für Reservierungen
Eine Reservierungshookfunktion, die mit [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook)installiert wird, wird jedes Mal aufgerufen, wenn Speicher zugeordnet, neu zugewiesen oder freigegeben wird. Diese Art von Hook kann für viele verschiedene Zwecke verwendet werden. Verwenden Sie es, um zu testen, wie eine Anwendung unzureichenden Arbeitsspeicher behandelt, z. b. zum Überprüfen von Zuweisungs Mustern oder zur Protokollierung von Zuordnungs Informationen für

> [!NOTE]
> Beachten Sie die Einschränkungen hinsichtlich der Verwendung von C-Laufzeitbibliotheksfunktionen in einer Zuweisungshookfunktion, die unter [Zuweisungshook und Speicherbelegungen von C-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) beschrieben werden.

 Eine Zuordnungs-Hook-Funktion sollte einen Prototyp wie das folgende Beispiel aufweisen:

```cpp
int YourAllocHook(int nAllocType, void *pvData,
        size_t nSize, int nBlockUse, long lRequest,
        const unsigned char * szFileName, int nLine )
```

 Der Zeiger, den Sie an [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) übergeben, ist vom Typ **_CRT_ALLOC_HOOK**, wie in „CRTDBG.H“ definiert:

```cpp
typedef int (__cdecl * _CRT_ALLOC_HOOK)
    (int, void *, size_t, int, long, const unsigned char *, int);
```

 Wenn die Lauf Zeit Bibliothek ihren Hook aufruft, gibt das *nAllocType* -Argument an, welcher Zuordnungs Vorgang durchgeführt werden soll ( **_HOOK_ALLOC**, **_HOOK_REALLOC**oder **_HOOK_FREE**). In einer freien oder in einer erneuten Zuordnung hat `pvData` einen Zeiger auf den Benutzer Artikel des Blocks, der freigegeben werden soll. Bei einer Zuordnung ist dieser Zeiger jedoch NULL, da die Zuordnung nicht aufgetreten ist. Die übrigen Argumente enthalten die Größe der fraglichen Zuordnung, den Blocktyp, die sequenzielle Anforderungs Nummer, die ihr zugeordnet ist, und einen Zeiger auf den Dateinamen. Wenn die Argumente verfügbar sind, enthalten Sie auch die Nummer der Zeile, in der die Zuordnung vorgenommen wurde. Nachdem die Hookfunktion die vom Autor vorgesehenen Analysen und sonstigen Aufgaben durchgeführt hat, muss sie entweder **TRUE** (der Zuweisungsvorgang kann fortgesetzt werden) oder **FALSE** (der Zuweisungsvorgang kann nicht durchgeführt werden) zurückgeben. Eine einfache Hookfunktion dieses Typs überprüft beispielsweise, wie viel Speicher bisher belegt wurde, und gibt **FALSE** zurück, wenn die Belegung ein geringes Maß überschritten hat. In der Anwendung würden dann diejenigen Reservierungsfehler auftreten, die normalerweise vorkommen, wenn sehr wenig Speicher verfügbar ist. Komplexere Hookfunktionen könnten Reservierungsmuster nachverfolgen, die Speichernutzung analysieren oder beim Auftreten bestimmter Situationen eine Meldung ausgeben.

## <a name="see-also"></a>Siehe auch

- [Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)