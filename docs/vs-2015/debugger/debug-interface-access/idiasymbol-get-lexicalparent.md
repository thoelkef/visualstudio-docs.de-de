---
title: 'Idiasymbol:: Get_lexicalparent | Microsoft-Dokumentation'
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
- IDiaSymbol::get_lexicalParent method
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0af84545fac88074aed90fe94c91a6a7d19de0f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735652"
---
# <a name="idiasymbolgetlexicalparent"></a>IDiaSymbol::get_lexicalParent
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft einen Verweis auf die übergeordnete lexikalische des Symbols ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das das übergeordnete lexikalische des Symbols darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder den Fehlercode.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Der übergeordnete lexikalische eines Symbols ist der einschließenden Funktion oder dieses Moduls. Lexikalische übergeordnet Funktionsparameter oder als lokale Variable ist z. B. die Funktion selbst, während das lexikalische übergeordnete Element der Funktion des Moduls ist, die, dem Sie in definiert ist.  
  
 Die möglichen Symbole, die angezeigt werden können, wie im übergeordneten lexikalischen Elemente dokumentiert werden [lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Lexikalische Hierarchie der Symboltypen](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)



