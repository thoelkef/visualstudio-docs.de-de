---
title: 'Idiasession:: Findsymbolbyrva | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVA method
ms.assetid: 14fb2903-b771-44d6-b0a8-44e0097c58ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9061a4f95e8bc70382185c9996c21524339fcaa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919953"
---
# <a name="idiasessionfindsymbolbyrva"></a>IDiaSession::findSymbolByRVA
Ruft einen bestimmtes Symbol-Typ, der enthält, oder um eine angegebene relative virtuelle Adresse (RVA) am nächsten ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT findSymbolByRVA (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `rva`  
 [in] Gibt an, die RVA.  
  
 `symtag`  
 [in] Der Symboltyp gefunden werden. Werte stammen aus der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md) Enumeration.  
  
 `ppSymbol`  
 [out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das Symbol darstellt, abgerufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
  
```C++  
IDiaSymbol* pFunc;  
pSession->findSymbolByRVA( rva, SymTagFunction, &pFunc );  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)