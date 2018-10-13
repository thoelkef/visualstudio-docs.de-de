---
title: Hookfunktionen für Clientblöcke | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 55b3200f93d5dd969687411f04ddca481ca099e9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49250685"
---
# <a name="client-block-hook-functions"></a>Hookfunktionen für Clientblöcke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



