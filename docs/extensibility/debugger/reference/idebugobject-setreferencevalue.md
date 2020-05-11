---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726379"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Legt den Referenzwert dieses Objekts fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Parameter
`pObject`\
[in] Ein [IDebugObject-Objekt,](../../../extensibility/debugger/reference/idebugobject.md) das den neuen Referenzwert darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode macht dieses [IDebugObject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) zu einem Verweis `pObject` auf den Wert des im Parameter angegebenen Objekts und wirft alle vorherigen Verweise weg. Beachten Sie, dass dieses `IDebugObject` Objekt bereits ein Verweistyp sein muss.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
