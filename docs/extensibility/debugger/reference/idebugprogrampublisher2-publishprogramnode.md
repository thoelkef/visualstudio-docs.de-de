---
title: IDebugProgramPublisher2::PublishProgramNode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::PublishProgramNode
helpviewer_keywords:
- IDebugProgramPublisher2::PublishProgramNode
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df68e72ee8597805bf02cb9c6e1c3a0bcaf8a449
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721668"
---
# <a name="idebugprogrampublisher2publishprogramnode"></a>IDebugProgramPublisher2::PublishProgramNode
Stellt einen Programmknoten für die Verwendung durch Debugmodule (DEs) und den Sitzungsdebug-Manager (SDM) zur Verfügung.

## <a name="syntax"></a>Syntax

```cpp
HRESULT PublishProgramNode(
   IDebugProgramNode2 *pProgramNode
);
```

```csharp
int PublishProgramNode(
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Parameter
`pProgramNode`\
[in] Ein [IDebugProgramNode2-Objekt,](../../../extensibility/debugger/reference/idebugprogramnode2.md) das den Programmknoten darstellt, der verfügbar gemacht werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Mit dieser Methode können Programme nach Informationen abgefragt werden, bevor sie zum Debuggen ausgewählt und gestartet werden.

 Um einen Programmknoten aus der Verfügbarkeit zu entfernen, rufen Sie die [UnpublishProgramNode-Methode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)
