---
title: 'Idiasession:: Symsareequiv | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91a3081cc32eb4286ed7b981dfa2a070dbf4a0ff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55036692"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Überprüft, um festzustellen, ob zwei Symbole entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `symbolA`  
 [in] Die erste [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das im Vergleich verwendet.  
  
 `symbolB`  
 [in] Die zweite `IDiaSymbol` Objekt, das im Vergleich verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt zurück, wenn die Symbole gleichwertig sind, `S_OK`ist, andernfalls gibt `S_FALSE`, die Symbole sind kein Äquivalent. Geben Sie andernfalls einen Fehlercode zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)