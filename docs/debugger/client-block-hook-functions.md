---
title: Hookfunktionen für Clientblöcke | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee0209c082185e111988e5f8e39f2f0b806a4995
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433118"
---
# <a name="client-block-hook-functions"></a>Hookfunktionen für Clientblöcke
Wenn Sie die in `_CLIENT_BLOCK`-Blöcken gespeicherten Daten überprüfen oder als Bericht ausgeben möchten, können Sie speziell für diesen Zweck eine Funktion schreiben. Der Prototyp dieser Funktion muss etwa wie der folgende, in CRTDBG.H definierte Prototyp aussehen:  
  
```cpp
void YourClientDump(void *, size_t)  
  
```  
  
 Das heißt, sollte die Hookfunktion akzeptieren einen **"void"** Zeiger auf den Anfang des Reservierungsblocks, zusammen mit einer **"size_t"** Typwert, der angibt, der die Reservierungsgröße und zurückgeben`void`. Der restliche Inhalt dieser Funktion ist Ihnen freigestellt.  
  
 Nachdem die Hookfunktion mithilfe der Installation [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), aufgerufen wird jedes Mal eine `_CLIENT_BLOCK` Block wird ausgegeben. Anschließend können Sie [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) zum Abrufen von Informationen zum Typ oder Untertyp der Dump ausgegebenen Blöcke.  
  
 Der Zeiger auf die Funktion, den Sie übergeben `_CrtSetDumpClient` ist vom Typ **_CRT_DUMP_CLIENT**, wie in CRTDBG.H definiert. H:  
  
```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2-Beispiel](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
