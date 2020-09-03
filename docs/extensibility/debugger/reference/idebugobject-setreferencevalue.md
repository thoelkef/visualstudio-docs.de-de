---
title: 'Idebugobject:: "abtreferencevalue" | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726379"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Legt den Verweis Wert dieses-Objekts fest.

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
in Ein [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, das den neuen Verweis Wert darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode macht dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt zu einem Verweis auf den Wert des Objekts, das im- `pObject` Parameter angegeben ist, und gibt einen vorherigen Verweis zurück. Beachten Sie, dass dieses `IDebugObject` Objekt bereits ein Referenztyp sein muss.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
