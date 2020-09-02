---
title: 'IDiaSession:: symsAreEquiv | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba8c77d7d97da75ce82fcbe732db64acf633b8af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150217"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prüft, ob zwei Symbole äquivalent sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `symbolA`  
 in Das erste [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das beim Vergleich verwendet wird.  
  
 `symbolB`  
 in Das zweite `IDiaSymbol` im Vergleich verwendete-Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Symbole äquivalent sind, wird zurückgegeben `S_OK` ; andernfalls wird zurückgegeben `S_FALSE` , die Symbole sind nicht äquivalent. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
