---
title: "IDiaSymbol::get_intro | Microsoft Docs"
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
  - "IDiaSymbol::get_intro-Methode"
ms.assetid: 101afe4a-4c57-45de-87b4-330394c6de10
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_intro
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob die Funktion eine einführende virtuelle Funktion ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_intro (   
   BOOL* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt `TRUE` zurück, wenn die Funktion die virtuelle Intro ist. andernfalls gibt `FALSE`zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Beispiel  
  
```cpp#  
class A {  
   virtual int f1();  
}  
class B : public A {  
   int f1();  
}  
```  
  
 `A::f1` sind und `B::f1` virtuelle Funktionen, aber `A::f1` ist die virtuelle Intro.  
  
## Anforderungen  
  
|Anforderung|Beschreibung|  
|-----------------|------------------|  
|Header:|dia2.h|  
|Version:|DIA SDK v7.0|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)