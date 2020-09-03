---
title: 'Idebugobject:: getmanageddebugobject | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726688"
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
vorgenommen Gibt ein [idebugmanagedobject](../../../extensibility/debugger/reference/idebugmanagedobject.md) -Objekt zurück, das das neu erstellte verwaltete-Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt E_FAIL zurück, wenn dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) keine Instanz einer verwalteten Wert Klasse darstellt.

## <a name="remarks"></a>Bemerkungen
 Dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt muss eine Instanz der verwalteten Wert Klasse, z. b. eine-Instanz, darstellen `System.Decimal` . Wenn eine lokale Kopie vorhanden ist, wird der Aufwand für das Aufrufen von [Evaluierungen](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) vermieden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
