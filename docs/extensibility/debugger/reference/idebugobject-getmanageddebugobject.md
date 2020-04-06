---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726688"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Erstellt eine Kopie des verwalteten Objekts im Adressraum des Debugmoduls.

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
[out] Gibt ein [IDebugManagedObject-Objekt](../../../extensibility/debugger/reference/idebugmanagedobject.md) zurück, das das neu erstellte verwaltete Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) keine Instanz für verwaltete Wertklassen darstellt.

## <a name="remarks"></a>Bemerkungen
 Dieses [IDebugObject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) muss eine verwaltete Wertklasseninstanz darstellen, z. B. eine `System.Decimal` Instanz. Durch eine lokale Kopie entfällt der Aufwand für den Aufruf von [Evaluate.](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
