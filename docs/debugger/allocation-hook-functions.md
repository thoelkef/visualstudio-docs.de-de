---
title: "Hookfunktionen für | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.hooks
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
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e00d43898fbc29ba238a670d39cf8d3e7638122
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2017
---
# <a name="allocation-hook-functions"></a>Hookfunktionen für Reservierungen
Einer Reservierungshookfunktion, installiert mit [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook), wird jedes Mal, wenn Arbeitsspeicher belegt, erneut reserviert oder freigegeben wird, aufgerufen. Dieser Hooktyp ist vielseitig verwendbar. Sie können damit beispielsweise testen, wie eine Anwendung auf Speichermangel reagiert, Reservierungsmuster überprüfen oder Reservierungsinformationen für die spätere Analyse protokollieren.  
  
> [!NOTE]
>  Beachten Sie die Einschränkung zur Verwendung von C-Laufzeitbibliotheksfunktionen in einer Reservierungshookfunktion, die in beschriebenen [Reservierungshooks und Speicherbelegungen von C Run-Time](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Der Prototyp einer Reservierungshookfunktion sollte etwa wie folgt aussehen:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Der Zeiger, die Sie zum übergeben [_CrtSetAllocHook](/cpp/c-runtime-library/reference/crtsetallochook) ist vom Typ **_CRT_ALLOC_HOOK**, wie in CRTDBG.H definiert. H  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Wenn die Laufzeitbibliothek Hook, ruft der *nAllocType* Argument angegeben, welche Vorgang ausgeführt werden, ist (**_HOOK_ALLOC**, **_HOOK_REALLOC**, oder **_HOOK_FREE**). Bei einer Freigabe oder einer erneuten Reservierung enthält `pvData` einen Zeiger auf den Benutzerbereich des freizugebenden Blocks. Im Falle einer Reservierung ist dieser Zeiger jedoch NULL, da die Reservierung noch nicht stattgefunden hat. Die übrigen Argumente enthalten die jeweilige Reservierungsgröße, den Blocktyp, die damit verknüpfte, fortlaufende Anforderungsnummer und ggf. einen Zeiger auf den Dateinamen und die Zeilennummer, in der die Reservierung durchgeführt wurde. Nachdem die Hookfunktion Analysen und sonstigen Aufgaben seine Autor nutzen will durchgeführt, muss er entweder zurückgeben **"true"**, die Reservierungsoperation kann fortgesetzt, oder **"false"**, dass, die fehlschlagen sollte. Eine einfache Hookfunktion dieses Typs überprüft der Menge an Speicher bisher belegt, und kehren zurück **"false"** , wenn die Belegung ein geringes überschritten hat. In der Anwendung würden dann diejenigen Reservierungsfehler auftreten, die normalerweise vorkommen, wenn sehr wenig Speicher verfügbar ist. Komplexere Hookfunktionen könnten Reservierungsmuster nachverfolgen, die Speichernutzung analysieren oder beim Auftreten bestimmter Situationen eine Meldung ausgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Reservierungshooks und Speicherbelegungen für C-Laufzeit](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
