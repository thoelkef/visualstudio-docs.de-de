---
title: IDebugArrayObject2::GetBaseIndizes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetBaseIndices
- IDebugArrayObject2::GetBaseIndices
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 925ce3a7bcce9f787e02c2bd2714f8b26d8cec26
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736154"
---
# <a name="idebugarrayobject2getbaseindices"></a>IDebugArrayObject2::GetBaseIndices
Ruft die Basisindizes (untere Grenzen) für jeden Index ab, wenn die Anzahl der Dimensionen im Array angegeben wird.

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

## <a name="parameters"></a>Parameter
`dwRank`\
[in] Die Anzahl der Dimensionen (Rang) des Arrays.

`dwIndices`\
[out] Die Basisindizes (untere Grenzen) für das Array.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Als Beispiel würde diese Funktion '5' für das Array zurückgeben, das durch den folgenden C-Code erstellt wurde:

```
int[] lengths = { 12 };
int[] lowerbounds = { 5 };
Array.CreateInstance(typeof(int), lengths, lowerbounds);
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)
