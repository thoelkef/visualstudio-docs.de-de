---
title: Hookfunktionen für Clientblöcke | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29bbfb24566a59047e47090f92a040c3c2fe8a12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513388"
---
# <a name="client-block-hook-functions"></a>Hookfunktionen für Clientblöcke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Clientblöcke](https://docs.microsoft.com/visualstudio/debugger/client-block-hook-functions).  
  
Wenn Sie die in `_CLIENT_BLOCK`-Blöcken gespeicherten Daten überprüfen oder als Bericht ausgeben möchten, können Sie speziell für diesen Zweck eine Funktion schreiben. Der Prototyp dieser Funktion muss etwa wie der folgende, in CRTDBG.H definierte Prototyp aussehen:  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Das heißt, sollte die Hookfunktion akzeptieren einen **"void"** Zeiger auf den Anfang des Reservierungsblocks, zusammen mit einer **"size_t"** Typwert, der angibt, der die Reservierungsgröße und zurückgeben`void`. Der restliche Inhalt dieser Funktion ist Ihnen freigestellt.  
  
 Nachdem die Hookfunktion mithilfe der Installation [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), aufgerufen wird jedes Mal eine `_CLIENT_BLOCK` Block wird ausgegeben. Anschließend können Sie [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) zum Abrufen von Informationen zum Typ oder Untertyp der Dump ausgegebenen Blöcke.  
  
 Der Zeiger auf die Funktion, den Sie übergeben `_CrtSetDumpClient` ist vom Typ **_CRT_DUMP_CLIENT**, wie in CRTDBG.H definiert. H:  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2-Beispiel](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)



