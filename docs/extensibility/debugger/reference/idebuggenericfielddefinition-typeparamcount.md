---
title: IDebugGenericFieldDefinition::TypeParamCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b753da4a418f13bb725ff5d7b0d2843fc314805b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324454"
---
# <a name="idebuggenericfielddefinitiontypeparamcount"></a>IDebugGenericFieldDefinition::TypeParamCount
Ruft die Anzahl von Typparametern, die dem generischen Feld zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT TypeParamCount(
   ULONG32* pcParams
);
```

```csharp
int TypeParamCount(
   ref uint pcParams
);
```

## <a name="parameters"></a>Parameter
`pcParams`\
[in, out] Die Anzahl von Typparametern.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn Liste\<T >, diese Methode gibt 1 zurück, und, falls Liste\<T1, T2 >, diese Methode gibt 2 zurück. Diese Methode gibt 0 zurück, wenn keine Typparameter vorhanden sind.

## <a name="see-also"></a>Siehe auch
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)