---
title: IDebugManagedObject::SetFromManagedObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dbaaf27222754d4a68d7de6367a2c0d7a1a8be73
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210633"
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