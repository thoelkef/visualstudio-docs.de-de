---
title: 'IDiaSession:: symbolById | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac409edcee7657e724822d1a72737c3142d8d93e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150203"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Symbol anhand seines eindeutigen Bezeichners ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 in Eindeutiger Bezeichner.  
  
 `ppSymbol`  
 vorgenommen Gibt ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt zurück, das das abgerufene Symbol darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Der angegebene Bezeichner ist ein eindeutiger Wert, der vom Dia SDK intern verwendet wird, um alle Symbole eindeutig zu machen.  
  
 Diese Methode kann z. b. verwendet werden, um das Symbol abzurufen, das den Typ eines anderen Symbols darstellt (siehe Beispiel).  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird ein [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt abgerufen, das den Typ eines anderen Symbols darstellt. Dieses Beispiel zeigt, wie die- `symbolById` Methode in der Sitzung verwendet wird. Ein einfacherer Ansatz besteht darin, die [idiasymmetribol:: get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) -Methode aufzurufen, um das Typsymbol direkt abzurufen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
