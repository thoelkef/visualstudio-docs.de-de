---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721171"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Erstellt eine eindeutige ID für diese Eigenschaft, um sicherzustellen, dass sie unter allen anderen Eigenschaften eindeutig ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird aufgerufen, wenn der Sitzungsdebug-Manager sicherstellen möchte, dass diese Eigenschaft unter allen anderen Eigenschaften eindeutig identifiziert wird. Das Debugmodul (DE) unterstützt diese Methode, es sei denn, die Eigenschaften, mit denen es sich befasst, sind bereits eindeutig identifiziert. Wenn die DE diese Methode nicht `E_NOTIMPL`unterstützt, wird zurückgegeben.

 Jede eindeutige `CreateObjectID` ID, die mit erstellt wird, wird zerstört, wenn die [DestroyObjectID-Methode](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) aufgerufen wird. dies signalisiert auch das Ende der Notwendigkeit, diese Eigenschaft eindeutig zu identifizieren.

> [!NOTE]
> Es gibt keine Methode zum Abrufen dieser eindeutigen ID, sodass die `CreateObjectID` DE bei eindeutigen IDs, wenn die Methode aufgerufen wird, alles tun kann, was sie möchte.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
