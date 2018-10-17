---
title: IDiaSymbol::get_isAcceleratorStubFunction | Microsoft-Dokumentation
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
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40ceb1c5d78d0f7a685f604b71c23915b1e8f4c3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200953"
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, ob das Symbol einem Symbol für die Funktion der obersten Ebene für einen Shader, der für eine Zugriffstaste, die entspricht, kompiliert entspricht einem `parallel_for_each` aufrufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 [out] Ein Zeiger auf eine `BOOL` , der angibt, ob das Symbol, die auf ein Symbol für die Funktion der obersten Ebene für einen Shader, der für eine Zugriffstaste, die entspricht, kompiliert entspricht einer `parallel_for_each` aufrufen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



