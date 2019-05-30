---
title: IDebugArrayField::GetNumberOfElements | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e8576c7f7365f8f87f8b31a90e414b75000026d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321740"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Ruft die Anzahl der Elemente im Array ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNumberOfElements( 
   DWORD* pdwNumElements
);
```

```csharp
int GetNumberOfElements(
   out uint pdwNumElements
);
```

## <a name="parameters"></a>Parameter
`pdwNumElements`\
[out] Gibt die Anzahl der Elemente im Array zurück.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der zurückgegebene Wert ist die Gesamtanzahl der Elemente im Array, unabhängig von der Anzahl von Dimensionen.

## <a name="see-also"></a>Siehe auch
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)