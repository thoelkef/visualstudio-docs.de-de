---
title: "IDiaSession::symbolById | Microsoft Docs"
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
  - "IDiaSession::symbolById-Methode"
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft ein Symbol mit seinem eindeutigen Bezeichner ab.  
  
## Syntax  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Parameter  
 `id`  
 \[in\]  Eindeutiger Bezeichner.  
  
 `ppSymbol`  
 \[out\]  Gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)\-Objekt zurück, das das abgerufene Symbol darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der angegebene Bezeichner ist ein eindeutiger Wert, der intern vom DIA SDK verwendet wird, um alle Symbole eindeutig zu machen.  
  
 Diese Methode kann verwendet werden, um beispielsweise das Symbol ab, das den Typ eines anderen Symbols darstellt \(siehe Beispiel\).  
  
## Beispiel  
 In diesem Beispiel wird [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) ab, das den Typ eines anderen Symbols darstellt.  Dieses Beispiel zeigt, wie die `symbolById`\-Methode in der Sitzung verwendet.  Ein einfacherer Ansatz besteht darin, die [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)\-Methode aufrufen, um das Symbol Typ direkt abzurufen.  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)