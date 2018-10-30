---
title: 'Idiasession:: Symsareequiv | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdaa1ab070b6d95af0f28f5bdaa005b9ac808766
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850983"
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