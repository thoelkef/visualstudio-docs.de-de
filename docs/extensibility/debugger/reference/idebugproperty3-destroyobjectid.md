---
title: IDebugProperty3::DestroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f465bc06712c5032c6e90288ebd02406de4f2330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721201"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Zerstört die eindeutige ID, die dieser Eigenschaft zugeordnet ist, was darauf hinweist, dass der Aufrufer diese Eigenschaft nicht mehr aus allen anderen Eigenschaften eindeutig identifizieren möchte.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn das Debugmodul keine eindeutigen IDs für eine Eigenschaft unterstützen muss (da es sie `E_NOTIMPL` bereits intern eindeutig nachverfolgt), kann es einfach für diese Methode zurückkehren.

 Eindeutige IDs werden mit einem Aufruf der [CreateObjectID-Methode](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) erstellt, wenn der Aufrufer sicherstellen möchte, dass diese Eigenschaft unter allen anderen Eigenschaften eindeutig identifiziert wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
