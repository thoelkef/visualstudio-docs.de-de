---
title: Hookfunktionen für Clientblöcke | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 711f7de86617f6574427a65c6efcef62c558306b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="client-block-hook-functions"></a>Hookfunktionen für Clientblöcke
Wenn Sie die in `_CLIENT_BLOCK`-Blöcken gespeicherten Daten überprüfen oder als Bericht ausgeben möchten, können Sie speziell für diesen Zweck eine Funktion schreiben. Der Prototyp dieser Funktion muss etwa wie der folgende, in CRTDBG.H definierte Prototyp aussehen:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 In anderen Worten, sollte die Hookfunktion akzeptieren ein **"void"** Zeiger auf den Anfang des Blocks Verteilung, das zusammen mit einer **Size_t** Typwert, der angibt, der die Reservierungsgröße und zurückgeben`void`. Der restliche Inhalt dieser Funktion ist Ihnen freigestellt.  
  
 Nachdem Sie die Hookfunktion mithilfe installiert haben [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), aufgerufen wird jedes Mal eine `_CLIENT_BLOCK` Block wird ausgegeben. Anschließend können Sie [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) Informationen auf den Typ oder Untertyp der Dump ausgegebenen Blöcke abrufen.  
  
 Der Zeiger auf die Funktion, den Sie übergeben `_CrtSetDumpClient` ist vom Typ **_CRT_DUMP_CLIENT**, wie in CRTDBG.H definiert. H  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2-Beispiel](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)