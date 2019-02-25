---
title: IDebugGenericFieldDefinition::TypeParamCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeParamCount
- IDebugGenericFieldDefinition::TypeParamCount
ms.assetid: d41dd5ea-aa25-4bf3-bcfd-e0bf451ead49
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e6334f727b0c40352b7e6ca9b9a199edd98a502
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690603"
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

#### <a name="parameters"></a>Parameter
 `pcParams`

 [in, out] Die Anzahl von Typparametern.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn Liste\<T >, diese Methode gibt 1 zurück, und, falls Liste\<T1, T2 >, diese Methode gibt 2 zurück. Diese Methode gibt 0 zurück, wenn keine Typparameter vorhanden sind.

## <a name="see-also"></a>Siehe auch
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)