---
title: 'Idiasession:: Symsareequiv | Microsoft-Dokumentation'
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
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb9b8833ca4e7d780677aca475ee13897dbb8fc8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780021"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Überprüft, um festzustellen, ob zwei Symbole entsprechen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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



