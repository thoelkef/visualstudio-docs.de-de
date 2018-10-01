---
title: 'Idialinenumber:: Get_compiland | Microsoft-Dokumentation'
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
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4a93c191aad5a87b4e58a0b799f7bcfd533a8e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524875"
---
# <a name="idialinenumbergetcompiland"></a>IDiaLineNumber::get_compiland
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idialinenumber:: Get_compiland](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialinenumber-get-compiland).  
  
Ruft einen Verweis auf das Symbol für der Kompiliereinheit, das die Bytes des Image Text beigetragen hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pRetVal  
 [out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt für der Kompiliereinheit, das die Bytes des Image Text beigetragen hat.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



