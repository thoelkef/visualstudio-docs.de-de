---
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 527f79724aeac0de58d0ae63c9c2408ed2eca9ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736163"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Ruft die Dimensionen des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDimensions( 
   DWORD dwCount,
   DWORD dwDimensions[]
);
```

```csharp
int GetDimensions(
   [In] uint    dwCount,
   [Out] uint[] dwDimensions
);
```

## <a name="parameters"></a>Parameter
`dwCount`\
[in] Die Anzahl der abzurufenden Dimensionen.

`dwDimensions`\
[in, out] Ein Array, das mit den Größen jeder Dimension gefüllt wird. `dwCount`gibt die maximale Größe `dwDimensions` des Arrays an.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein mehrdimensionales Array kann für jede Dimension unterschiedliche Größen aufweisen. Wenn sie z. B. `myarray[3][2][6]`das dreidimensionale Array erhält, würde diese `dwDimensions` Methode 3, 2 und 6 im Parameter in dieser Reihenfolge zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
