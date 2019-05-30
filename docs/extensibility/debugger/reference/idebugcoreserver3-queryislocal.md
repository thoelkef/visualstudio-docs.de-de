---
title: IDebugCoreServer3::QueryIsLocal | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92ef0e0016027bb8e5d60ee8df070095da72d7ab
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343973"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
Bestimmt, ob der Server an den Aufrufer lokal ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Rückgabewert
 Gibt `S_OK` an der Server lokal ist. Gibt `S_FALSE` , wenn der Server von einer Instanz von msvsmon.exe, ausgeführt wird, die in der Regel für das Remotedebugging verwendet wird.

## <a name="see-also"></a>Siehe auch
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)