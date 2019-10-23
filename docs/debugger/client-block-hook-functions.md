---
title: Hookfunktionen für Client Blöcke | Microsoft-Dokumentation
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
ms.openlocfilehash: 5b7b0ef177922f09239c8925ced1ca013e966c0e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745716"
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
- [crt_dbg2, Beispiel](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)