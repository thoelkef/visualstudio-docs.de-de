---
title: 'Idiasession:: Symbolbyid | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60b7495abd70eb7e02408cfe711701ec15f5ac4b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272713"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Symbol durch seinen eindeutigen Bezeichner ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 [in] Eindeutiger Bezeichner.  
  
 `ppSymbol`  
 [out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das Symbol darstellt, abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der angegebene Bezeichner ist ein eindeutiger Wert wird intern vom DIA-SDK verwendet, um alle Symbole eindeutig zu machen.  
  
 Diese Methode kann verwendet werden, z. B. das Symbol, der den Typ der ein anderes Symbol abrufen (siehe Beispiel).  
  
## <a name="example"></a>Beispiel  
 Ruft ab, in diesem Beispiel wird ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , die den Typ der ein anderes Symbol darstellt. Dieses Beispiel zeigt, wie Sie mit der `symbolById` -Methode in der Sitzung. Ein einfacher Ansatz ist, rufen Sie die [idiasymbol:: Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) Methode, um das Typsymbol direkt abrufen.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)



