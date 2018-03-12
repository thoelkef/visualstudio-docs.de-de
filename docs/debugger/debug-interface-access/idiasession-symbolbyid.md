---
title: 'Idiasession:: Symbolbyid | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c6792f3271f09742d40b92691dee06854deea8f2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Ruft ein Symbol, das durch seinen eindeutigen Bezeichner ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 [in] Der eindeutige Bezeichner.  
  
 `ppSymbol`  
 [out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) abgerufene Objekt, das das Symbol darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der angegebene Bezeichner ist ein eindeutiger Wert, der durch das DIA SDK Intern verwendet wird, um alle Symbole eindeutig zu machen.  
  
 Diese Methode kann verwendet werden, z. B. auf das Symbol für den Typ des ein anderes Symbol abrufen (siehe Beispiel).  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel ruft eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , die den Typ des ein anderes Symbol darstellt. Dieses Beispiel zeigt, wie die `symbolById` Methode in der Sitzung. Ein einfacherer Ansatz ist das Aufrufen der [idiasymbol:: Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) Methode, um das Typsymbol direkt abzurufen.  
  
```C++  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)