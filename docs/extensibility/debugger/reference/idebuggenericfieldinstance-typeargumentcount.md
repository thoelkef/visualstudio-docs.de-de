---
title: IDebugGenericFieldInstance::TypeArgumentCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5a6b55d51cd2db25da1b51af84172d64c682245
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689940"
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Gibt die Anzahl der Parameterargumente für diese Instanz zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT TypeArgumentCount(
   ULONG32* pcArgs
);
```

```csharp
int TypeArgumentCount(
   ref uint pcArgs
);
```

#### <a name="parameters"></a>Parameter
 `pcArgs`

 [in, out] Die Anzahl von Typargumenten für Parameter für diese Instanz.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Z. B. wenn Liste\<Int >, diese Methode gibt 1 zurück, und, falls Liste\<Int, float2 > Diese Methode gibt 2 zurück. Diese Methode gibt 0 zurück, wenn keine Argumente des Typs vorhanden sind.

## <a name="see-also"></a>Siehe auch
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)