---
title: IDebugArrayObject2::GetBaseIndices | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5355e85007c04e523efa4030ca0603a01cf88c68
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704058"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Ruft den Basis-Indizes (untere Grenzen) für jeden Index in Anbetracht der Anzahl der Dimensionen im Array ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBaseIndices (
   DWORD  dwRank,
   DWORD* dwIndices
);
```

```csharp
int GetBaseIndices (
   uint       dwRank,
   out uint[] dwIndices
);
```

#### <a name="parameters"></a>Parameter
 `dwRank`

 [in] Die Anzahl der Dimensionen (Rang) des Arrays.

 `dwIndices`

 [out] Die Basis Indizes (untere Grenzen) für das Array.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Beispielsweise würde diese Funktion "5" zurück, für das Array erstellt folgende C# Code:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Siehe auch
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)