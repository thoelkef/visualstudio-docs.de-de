---
title: IDebugArrayObject::GetRank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c645683cf1f842afdecba3c3dee8942a3fd6971a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736189"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Ruft den Rang des Arrays ab, d. h. die Anzahl der Dimensionen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parameter
`pdwRank`\
[out] Gibt den Rang zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Verwenden Sie die [GetDimensions-Methode,](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) um die Größe jeder Dimension des Arrayobjekts abzurufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
