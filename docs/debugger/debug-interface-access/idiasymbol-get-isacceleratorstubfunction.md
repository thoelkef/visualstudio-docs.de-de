---
title: IDiaSymbol::get_isAcceleratorStubFunction | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bbcfbfcd1e95a45388d0b7c0626f1cd529607ce4
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836628"
---
# <a name="idiasymbolgetisacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Gibt an, ob das Symbol einem Symbol für die Funktion der obersten Ebene für einen Shader, der für eine Zugriffstaste, die entspricht, kompiliert entspricht einem `parallel_for_each` aufrufen.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

[out] Ein Zeiger auf eine `BOOL` , der angibt, ob das Symbol, die auf ein Symbol für die Funktion der obersten Ebene für einen Shader, der für eine Zugriffstaste, die entspricht, kompiliert entspricht einer `parallel_for_each` aufrufen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)