---
title: "IDiaLineNumber::get_columnNumberEnd | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaLineNumber::get_columnNumberEnd-Methode"
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLineNumber::get_columnNumberEnd
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die 1\-basierte Sources spaltennummer in der die Ausdrucks\- oder Anweisung beendet wird.  
  
## Syntax  
  
```cpp#  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Die Spaltennummer in der die Ausdrucks\- oder \- Anweisung endet zurückgibt.  Wenn der Wert null ist, sind die Spalten Informationen zum Beenden nicht vorhanden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Spaltenwert, der von dieser Methode zurückgegeben wird, ist ein Byteoffset in der Zeile auf die Position hinter dem letzten Zeichen der Anweisung in der Zeile.  
  
## Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)