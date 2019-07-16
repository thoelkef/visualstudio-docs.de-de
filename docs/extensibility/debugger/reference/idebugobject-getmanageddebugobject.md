---
title: IDebugObject::GetManagedDebugObject | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 98bf0054f02ff85f67f21cd817309bb569dfe678
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323759"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Erstellt eine Kopie des verwalteten Objekts im Adressraum der Debug-Engine.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>Parameter
`ppObject`\
[out] Gibt eine [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) Objekt, das das neu erstellte verwaltete Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn diese [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) stellt keine Instanz einer verwalteten Klasse dar.

## <a name="remarks"></a>Hinweise
 Dies [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt muss eine Klasseninstanz verwalteten Wert darstellen, z. B. eine `System.Decimal` Instanz. Indem Sie eine lokale Kopie, den Aufwand des Aufrufs [auswerten](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) wird gelöscht.

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)