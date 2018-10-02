---
title: Hookfunktionen für | Microsoft-Dokumentation
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
- memory allocation, logging allocation information
- insufficient memory
- debugging [C++], hook functions
- _CrtSetAllocHook function
- allocation hooks
- hooks, allocation
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c42d1984d8138186241fddaf3d8dbaee7f02338d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524250"
---
# <a name="allocation-hook-functions"></a>Hookfunktionen für Reservierungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Hookfunktionen](https://docs.microsoft.com/visualstudio/debugger/allocation-hook-functions).  
  
Einer Reservierungshookfunktion, installiert mit [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), wird jedes Mal aufgerufen Arbeitsspeicher reserviert, erneut belegt oder freigegeben ist. Dieser Hooktyp ist vielseitig verwendbar. Sie können damit beispielsweise testen, wie eine Anwendung auf Speichermangel reagiert, Reservierungsmuster überprüfen oder Reservierungsinformationen für die spätere Analyse protokollieren.  
  
> [!NOTE]
>  Beachten Sie die Einschränkung zur Verwendung von C-Laufzeitbibliotheksfunktionen in einer Reservierungshookfunktion, die in beschriebenen [Reservierungshooks und Speicherreservierungen von C Run-Time](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Der Prototyp einer Reservierungshookfunktion sollte etwa wie folgt aussehen:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Der Zeiger, der Sie übergeben [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) ist vom Typ **_CRT_ALLOC_HOOK**, wie in CRTDBG.H definiert. H:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Wenn die Laufzeitbibliothek die Hookfunktion aufruft, wird die *nAllocType* Argument gibt an, welche Vorgang ist, ausgeführt werden (**_HOOK_ALLOC**, **_HOOK_REALLOC**, oder **_HOOK_FREE**). Bei einer Freigabe oder einer erneuten Reservierung enthält `pvData` einen Zeiger auf den Benutzerbereich des freizugebenden Blocks. Im Falle einer Reservierung ist dieser Zeiger jedoch NULL, da die Reservierung noch nicht stattgefunden hat. Die übrigen Argumente enthalten die jeweilige Reservierungsgröße, den Blocktyp, die damit verknüpfte, fortlaufende Anforderungsnummer und ggf. einen Zeiger auf den Dateinamen und die Zeilennummer, in der die Reservierung durchgeführt wurde. Nachdem die Hookfunktion Analysen führt und andere der Autor möchte Aufgaben, muss er entweder zurückgeben **"true"**, die Reservierungsoperation kann fortgesetzt, oder **"false"**, um anzugeben, die die Vorgang sollte fehlschlagen. Eine einfache Hookfunktion dieses Typs überprüfen Sie die Menge an Speicher bisher belegt, und kehren zurück **"false"** , wenn die Belegung ein geringes Maß überschritten hat. In der Anwendung würden dann diejenigen Reservierungsfehler auftreten, die normalerweise vorkommen, wenn sehr wenig Speicher verfügbar ist. Komplexere Hookfunktionen könnten Reservierungsmuster nachverfolgen, die Speichernutzung analysieren oder beim Auftreten bestimmter Situationen eine Meldung ausgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Reservierungshooks und Speicherreservierungen von C-Laufzeit](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2-Beispiel](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)



