---
title: "IDiaSession::findLines | Microsoft Docs"
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
  - "IDiaSession::findLines-Methode"
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findLines
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Zeilennummern und innerhalb der angegebenen Kompiliereinheits\- Bezeichner der Quelldatei ab oder legt diese fest.  
  
## Syntax  
  
```cpp#  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parameter  
 `compiland`  
 \[in\]Ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt, das die Kompiliereinheit darstellt.  Verwenden Sie diese Schnittstelle als Kontext, in dem für die Zeilennummern suchen.  
  
 `file`  
 \[in\]  Ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)\-Objekt, das die Quelldatei darstellt, die für die Zeilennummern zu suchen.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)\-Objekt zurück, das eine Liste der abgerufenen Zeilennummern enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)