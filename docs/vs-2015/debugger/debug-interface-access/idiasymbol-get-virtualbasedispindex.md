---
title: 'Idiasymbol:: Get_virtualbasedispindex | Microsoft-Dokumentation'
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
- IDiaSymbol::get_virtualBaseDispIndex method
ms.assetid: 5561a3cb-2c82-41cf-9217-3ee2b1e1d1d1
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92b0b9cb58a1d8e3db2551902a353f74a447b53b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239498"
---
# <a name="idiasymbolgetvirtualbasedispindex"></a>IDiaSymbol::get_virtualBaseDispIndex
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Index des Symbols in der virtuellen Basis Verschiebung-Tabelle ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_virtualBaseDispIndex (  
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Index in die virtuelle Basisklasse Verschiebung-Tabelle.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



