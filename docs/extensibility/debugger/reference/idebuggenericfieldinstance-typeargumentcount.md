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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e881996a30d7d18751734f07fc40b6be7a299b26
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66198896"
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

## <a name="parameters"></a>Parameter
`pcArgs`\
[in, out] Die Anzahl von Typargumenten für Parameter für diese Instanz.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Z. B. wenn Liste\<Int >, diese Methode gibt 1 zurück, und, falls Liste\<Int, float2 > Diese Methode gibt 2 zurück. Diese Methode gibt 0 zurück, wenn keine Argumente des Typs vorhanden sind.

## <a name="see-also"></a>Siehe auch
- [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)