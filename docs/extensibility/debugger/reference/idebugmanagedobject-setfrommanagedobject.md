---
title: 'Idebugmanagedobject:: setfrommanagedobject | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4056befa0b5b053d480983901b24feb6b25cf538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727698"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Legt den Wert der Instanz des Value-Klassen Objekts von der Instanz der Wert Klasse fest, die als Parameter bereitgestellt wird.

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
in Eine-Schnittstelle, die das verwaltete Objekt darstellt, das den neuen Wert enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird verwendet, um das verwaltete Objekt entsprechend der Darstellung durch das [idebugmanagedobject](../../../extensibility/debugger/reference/idebugmanagedobject.md) -Objekt zu ändern.

## <a name="see-also"></a>Weitere Informationen
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
