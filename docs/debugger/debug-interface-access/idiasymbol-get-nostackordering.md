---
title: "IDiaSymbol::get_noStackOrdering | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_noStackOrdering-Methode"
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_noStackOrdering
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Diese Funktion ruft ein Flag ab, das angibt, ob Keine Stapelreihenfolge als Teil der Stapel Puffer der Überprüfung \([\/GS \(Puffer\-Sicherheitsüberprüfung\)](/visual-cpp/build/reference/gs-buffer-security-check)\-Compileroption\) durchgeführt werden konnte.  
  
## Syntax  
  
```cpp#  
HRESULT get_noStackOrdering(  
   BOOL *pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt `TRUE` zurück, wenn keine Stapelreihenfolge als Teil der Stapel Puffer der Überprüfung durchgeführt werden konnte. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v8.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [\/GS \(Puffer\-Sicherheitsüberprüfung\)](/visual-cpp/build/reference/gs-buffer-security-check)