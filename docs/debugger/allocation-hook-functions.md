---
title: "Hookfunktionen f&#252;r Reservierungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_CrtSetAllocHook-Funktion"
  - "Reservierungshooks"
  - "Debuggen [C++], Hookfunktionen"
  - "Hooks, Reservierung"
  - "Nicht genügend Speicher"
  - "Speicherreservierung, Protokollieren von Reservierungsinformationen"
ms.assetid: 6bfbdb65-8cb1-4c21-8c45-7194a2b77c1e
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Hookfunktionen f&#252;r Reservierungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine mithilfe von [\_CrtSetAllocHook](/visual-cpp/c-runtime-library/reference/crtsetallochook) installierte Hookfunktion für Reservierungen wird jedes Mal aufgerufen, wenn Speicher belegt, erneut belegt oder freigegeben wird.  Dieser Hooktyp ist vielseitig verwendbar.  Sie können damit beispielsweise testen, wie eine Anwendung auf Speichermangel reagiert, Reservierungsmuster überprüfen oder Reservierungsinformationen für die spätere Analyse protokollieren.  
  
> [!NOTE]
>  Beachten Sie die Einschränkungen hinsichtlich der Verwendung von C\-Laufzeitbibliotheksfunktionen in einer Reservierungshookfunktion. Siehe dazu [Reservierungshooks und Speicherbelegungen von C\-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md).  
  
 Der Prototyp einer Reservierungshookfunktion sollte etwa wie folgt aussehen:  
  
```  
int YourAllocHook(int nAllocType, void *pvData,  
        size_t nSize, int nBlockUse, long lRequest,  
        const unsigned char * szFileName, int nLine )  
```  
  
 Der Zeiger, den Sie an [\_CrtSetAllocHook](/visual-cpp/c-runtime-library/reference/crtsetallochook) übergeben, ist vom Typ **\_CRT\_ALLOC\_HOOK**, wie in CRTDBG.H definiert:  
  
```  
typedef int (__cdecl * _CRT_ALLOC_HOOK)  
    (int, void *, size_t, int, long, const unsigned char *, int);  
```  
  
 Wenn die Laufzeitbibliothek die Hookfunktion aufruft, wird durch das *nAllocType*\-Argument angegeben, welche Reservierungsoperation \(**\_HOOK\_ALLOC**, **\_HOOK\_REALLOC** oder **\_HOOK\_FREE**\) ausgeführt werden soll.  Bei einer Freigabe oder einer erneuten Reservierung enthält `pvData` einen Zeiger auf den Benutzerbereich des freizugebenden Blocks.  Im Falle einer Reservierung ist dieser Zeiger jedoch NULL, da die Reservierung noch nicht stattgefunden hat.  Die übrigen Argumente enthalten die jeweilige Reservierungsgröße, den Blocktyp, die damit verknüpfte, fortlaufende Anforderungsnummer und ggf. einen Zeiger auf den Dateinamen und die Zeilennummer, in der die Reservierung durchgeführt wurde.  Nachdem die Hookfunktion die vom Autor vorgesehenen Analysen und sonstigen Aufgaben durchgeführt hat, muss sie entweder **TRUE** \(die Reservierungsoperation kann fortgesetzt werden\) oder **FALSE** \(die Reservierungsoperation wird fehlschlagen\) zurückgeben.  Eine einfache Hookfunktion dieses Typs überprüft beispielsweise, wie viel Speicher bisher belegt wurde, und gibt **FALSE** zurück, wenn die Belegung ein geringes Maß überschritten hat.  In der Anwendung würden dann diejenigen Reservierungsfehler auftreten, die normalerweise vorkommen, wenn sehr wenig Speicher verfügbar ist.  Komplexere Hookfunktionen könnten Reservierungsmuster nachverfolgen, die Speichernutzung analysieren oder beim Auftreten bestimmter Situationen eine Meldung ausgeben.  
  
## Siehe auch  
 [Reservierungshooks und Speicherreservierungen von C\-Laufzeitbibliotheken](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)   
 [Schreiben von Hookfunktionen zum Debuggen](../debugger/debug-hook-function-writing.md)   
 [crt\_dbg2 Sample](http://msdn.microsoft.com/de-de/21e1346a-6a17-4f57-b275-c76813089167)