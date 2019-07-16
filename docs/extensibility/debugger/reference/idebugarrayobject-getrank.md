---
title: IDebugArrayObject::GetRank | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a733baf1be2e5a249c214547b31465bb2464ed6
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "66351782"
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Ruft den Rang des Arrays, d. h. die Anzahl der Dimensionen ab.

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
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Verwenden der [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) Methode, um die Größe der einzelnen Dimensionen des Array-Objekt abzurufen.

## <a name="see-also"></a>Siehe auch
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)