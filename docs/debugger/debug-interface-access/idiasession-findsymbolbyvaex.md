---
title: "IDiaSession::findSymbolByVAEx | Microsoft Docs"
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
  - "IDiaSession::findSymbolByVAEx-Methode"
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSession::findSymbolByVAEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen angegebenen Symbol, der den Typ enthält am nächsten ist, ab oder für eine angegebene virtuelle Adresse \(VA\) und Offset.  
  
## Syntax  
  
```cpp#  
HRESULT findSymbolByVAEx (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### Parameter  
 `va`  
 \[in\]  Gibt das VA an.  
  
 `symtag`  
 \[in\]  Symbol Gesucht werden soll.  Werte werden von der [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)\-Enumeration bestimmt.  
  
 `ppSymbol`  
 \[out\]  Gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt zurück, das das abgerufene Symbol darstellt.  
  
 `displacement`  
 \[out\]  Gibt einen Wert zurück, der einem Offset von virtuellen Adresse angibt, die von `va`angegeben ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );  
```  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)