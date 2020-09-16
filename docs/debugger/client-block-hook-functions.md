---
title: Hookfunktionen für Clientblöcke | Microsoft-Dokumentation
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
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 881809dda7e8254f9d337b68f0c317eccfd9093d
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600194"
---
# <a name="client-block-hook-functions"></a>Hookfunktionen für Clientblöcke
Wenn Sie die in `_CLIENT_BLOCK`-Blöcken gespeicherten Daten überprüfen oder als Bericht ausgeben möchten, können Sie speziell für diesen Zweck eine Funktion schreiben. Der Prototyp dieser Funktion muss etwa wie der folgende, in CRTDBG.H definierte Prototyp aussehen:

```cpp
void YourClientDump(void *, size_t)
```

 Das bedeutet, dass die Hookfunktion einen **void**-Zeiger auf den Anfang des Zuweisungsblocks sowie einen Wert vom Typ **size_t**, der die Zuweisungsgröße angibt, akzeptieren und `void` zurückgeben muss. Der restliche Inhalt dieser Funktion ist Ihnen freigestellt.

 Nachdem Sie die Hookfunktion mithilfe von [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient) installiert haben, wird sie bei jedem Dump eines `_CLIENT_BLOCK`-Blocks aufgerufen. Mithilfe von [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) können Sie anschließend Informationen zum Typ oder Untertyp der im Dump ausgegebenen Blöcke abrufen.

 Der Zeiger auf die Funktion, den Sie an `_CrtSetDumpClient` übergeben, ist vom Typ **_CRT_DUMP_CLIENT**, wie in „CRTDBG.H“ definiert:

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Siehe auch

- [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)
- [crt_dbg2, Beispiel](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)