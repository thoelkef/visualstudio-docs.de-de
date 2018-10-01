---
title: 'Idiasession:: Symsareequiv | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08b091bfca65c2713f822e50a2bcacb5ac3df587
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522986"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasession:: Symsareequiv](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasession-symsareequiv).  
  
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



