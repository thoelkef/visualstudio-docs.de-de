---
title: 'Idiasymmetribol:: get_isAcceleratorStubFunction | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69f82f836be6ab91fe73af5a0febf7a39723b191
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199896"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, ob das Symbol einem Funktions Symbol der obersten Ebene für einen Shader entspricht, der für eine Zugriffstaste kompiliert wurde, die einem-Befehl entspricht `parallel_for_each` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_isAcceleratorStubFunction(   
   BOOL* pFlag);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 vorgenommen Ein Zeiger auf einen `BOOL` , der angibt, ob das Symbol einem Funktions Symbol der obersten Ebene für einen Shader entspricht, der für eine Zugriffstaste kompiliert wurde, die einem-Befehl entspricht `parallel_for_each` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
