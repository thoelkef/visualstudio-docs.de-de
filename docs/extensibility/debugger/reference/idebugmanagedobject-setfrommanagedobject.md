---
title: IDebugManagedObject::SetFromManagedObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf82275bf3375098cc8a8bcbeb200846252d2cec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349378"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Legt den Wert der Instanz des Klassenobjekts Wert aus der Instanz der Wertklasse als Parameter angegeben.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

## <a name="parameters"></a>Parameter
`pManagedObject`\
[in] Eine Schnittstelle, die das verwaltete Objekt, das mit dem neuen Wert darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird verwendet, um das verwaltete Objekt zu ändern, dargestellt durch die [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) Objekt.

## <a name="see-also"></a>Siehe auch
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)