---
title: IDebugArrayObject::GetRank | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetRank
helpviewer_keywords:
- IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf9700e2c3b29561229999506ed789a2e3d6e52e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423672"
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

#### <a name="parameters"></a>Parameter
 `pdwRank`

 [out] Gibt den Rang zurück.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Verwenden der [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) Methode, um die Größe der einzelnen Dimensionen des Array-Objekt abzurufen.

## <a name="see-also"></a>Siehe auch
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)