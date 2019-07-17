---
title: IDebugManagedObject::GetManagedObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74390d4c5f27400b0549408b1c36e9e385b3e60b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180605"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Gibt eine Schnittstelle, die das verwaltete Objekt darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

#### <a name="parameters"></a>Parameter
 `ppManagedObject`

 [out] Gibt eine Schnittstelle, die das verwaltete Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Schnittstelle, die von dieser Methode zurückgegebene kann für alle von der verwalteten Klasse, die zugehörigen Methoden, die aufgerufen werden, sodass implementierte Schnittstelle abgefragt werden.

## <a name="see-also"></a>Siehe auch
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)