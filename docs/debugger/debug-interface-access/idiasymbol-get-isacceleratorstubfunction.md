---
title: 'Idiasymmetribol:: get_isAcceleratorStubFunction | Microsoft-Dokumentation'
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
ms.openlocfilehash: baf71d3be8916c18b16e4022a2af884617b5fd70
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740308"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Gibt an, ob das Symbol einem Funktions Symbol der obersten Ebene für einen Shader entspricht, der für eine Zugriffstaste kompiliert wurde, die einem `parallel_for_each`-Befehl entspricht.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Ein Zeiger auf einen `BOOL` der angibt, ob das Symbol einem Funktions Symbol der obersten Ebene für einen Shader entspricht, der für eine Zugriffstaste kompiliert wurde, die einem `parallel_for_each`-Befehl entspricht.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)