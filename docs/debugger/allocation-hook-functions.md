---
title: Hookfunktionen für | Microsoft-Dokumentation
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
ms.openlocfilehash: 406647ae086285df8dfdfc00daf4b62be66e74a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402698"
---
# <a name="allocation-hook-functions"></a>Hookfunktionen für Reservierungen
Einer Reservierungshookfunktion, installiert mit [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), wird jedes Mal aufgerufen Arbeitsspeicher reserviert, neu zugeordnet oder freigegeben wird. Sie können diese Art von Hook für unterschiedliche Zwecke verwenden. Verwenden Sie, um zu testen, wie eine Anwendung nicht genügend Arbeitsspeicher Situationen, z. B. verhält, Reservierungsmuster überprüfen oder protokollieren Sie Reservierungsinformationen für die spätere Analyse.

> [!NOTE]
> Beachten Sie die Einschränkungen hinsichtlich der Verwendung von C-Laufzeitbibliotheksfunktionen in einer Zuweisungshookfunktion, die unter [Zuweisungshook und Speicherbelegungen von C-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) beschrieben werden.

 Eine Reservierungshookfunktion sollte einen Prototyp wie im folgenden Beispiel haben:

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

 Wenn die Laufzeitbibliothek die Hookfunktion aufruft, wird die *nAllocType* Argument gibt an, welche Vorgang ist gemacht werden sollen (**_HOOK_ALLOC**, **_HOOK_REALLOC**, oder **_HOOK_FREE**). In einer kostenlosen oder in einer erneuten Reservierung `pvData` verfügt über einen Zeiger auf den Benutzer Artikel des freizugebenden Blocks. Ist jedoch einer Reservierung ist dieser Zeiger null ist, da die Zuordnung aufgetreten ist, wurde nicht. Die übrigen Argumente enthalten die Größe der jeweilige Reservierungsgröße, den Blocktyp, die fortlaufende Anforderungsnummer zugeordnet sind, und ein Zeiger auf den Dateinamen an. Falls verfügbar, enthalten die Argumente auch die Nummer der Zeile, in der die Reservierung durchgeführt wurde. Nachdem die Hookfunktion die vom Autor vorgesehenen Analysen und sonstigen Aufgaben durchgeführt hat, muss sie entweder **TRUE** (der Zuweisungsvorgang kann fortgesetzt werden) oder **FALSE** (der Zuweisungsvorgang kann nicht durchgeführt werden) zurückgeben. Eine einfache Hookfunktion dieses Typs überprüft beispielsweise, wie viel Speicher bisher belegt wurde, und gibt **FALSE** zurück, wenn die Belegung ein geringes Maß überschritten hat. In der Anwendung würden dann diejenigen Reservierungsfehler auftreten, die normalerweise vorkommen, wenn sehr wenig Speicher verfügbar ist. Komplexere Hookfunktionen könnten Reservierungsmuster nachverfolgen, die Speichernutzung analysieren oder beim Auftreten bestimmter Situationen eine Meldung ausgeben.

## <a name="see-also"></a>Siehe auch

- [Reservierungshooks und Speicherreservierungen von C-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)
- [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)