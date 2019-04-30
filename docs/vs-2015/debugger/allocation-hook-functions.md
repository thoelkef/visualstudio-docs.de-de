---
title: Hookfunktionen für | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b617f0c154c14113370fff257c6837ce8314134a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439930"
---
# <a name="allocation-hook-functions"></a>Hookfunktionen für Reservierungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Einer Reservierungshookfunktion, installiert mit [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d), wird jedes Mal aufgerufen Arbeitsspeicher reserviert, erneut belegt oder freigegeben ist. Dieser Hooktyp ist vielseitig verwendbar. Sie können damit beispielsweise testen, wie eine Anwendung auf Speichermangel reagiert, Reservierungsmuster überprüfen oder Reservierungsinformationen für die spätere Analyse protokollieren.  
  
> [!NOTE]
> Beachten Sie die Einschränkungen hinsichtlich der Verwendung von C-Laufzeitbibliotheksfunktionen in einer Zuweisungshookfunktion, die unter [Zuweisungshook und Speicherbelegungen von C-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md) beschrieben werden.  
  
 Der Prototyp einer Reservierungshookfunktion sollte etwa wie folgt aussehen:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Der Zeiger, den Sie an [_CrtSetAllocHook](http://msdn.microsoft.com/library/405df37b-2fd1-42c8-83bc-90887f17f29d) übergeben, ist vom Typ **_CRT_ALLOC_HOOK**, wie in „CRTDBG.H“ definiert:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Wenn die Laufzeitbibliothek die Hookfunktion aufruft, wird die *nAllocType* Argument gibt an, welche Vorgang ist, ausgeführt werden (**_HOOK_ALLOC**, **_HOOK_REALLOC**, oder **_HOOK_FREE**). Bei einer Freigabe oder einer erneuten Reservierung enthält `pvData` einen Zeiger auf den Benutzerbereich des freizugebenden Blocks. Im Falle einer Reservierung ist dieser Zeiger jedoch NULL, da die Reservierung noch nicht stattgefunden hat. Die übrigen Argumente enthalten die jeweilige Reservierungsgröße, den Blocktyp, die damit verknüpfte, fortlaufende Anforderungsnummer und ggf. einen Zeiger auf den Dateinamen und die Zeilennummer, in der die Reservierung durchgeführt wurde. Nachdem die Hookfunktion die vom Autor vorgesehenen Analysen und sonstigen Aufgaben durchgeführt hat, muss sie entweder **TRUE** (der Zuweisungsvorgang kann fortgesetzt werden) oder **FALSE** (der Zuweisungsvorgang kann nicht durchgeführt werden) zurückgeben. Eine einfache Hookfunktion dieses Typs überprüft beispielsweise, wie viel Speicher bisher belegt wurde, und gibt **FALSE** zurück, wenn die Belegung ein geringes Maß überschritten hat. In der Anwendung würden dann diejenigen Reservierungsfehler auftreten, die normalerweise vorkommen, wenn sehr wenig Speicher verfügbar ist. Komplexere Hookfunktionen könnten Reservierungsmuster nachverfolgen, die Speichernutzung analysieren oder beim Auftreten bestimmter Situationen eine Meldung ausgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuweisungshooks und Speicherbelegungen von C-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, Beispiel](http://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
