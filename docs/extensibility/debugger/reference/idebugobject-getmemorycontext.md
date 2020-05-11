---
title: IDebugObject::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16427685765c1471fba3993743efc204cb99c367
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726659"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Ruft den Speicherkontext ab, der die Adresse des Objektwerts darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>Parameter
`pContext`\
[out] Gibt ein [IDebugMemoryContext2-Objekt](../../../extensibility/debugger/reference/idebugmemorycontext2.md) zurück, das die Adresse des Objektwerts darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der zurückgegebene Speicherkontext gibt die Adresse des Werts an, der durch dieses [IDebugObject-Objekt](../../../extensibility/debugger/reference/idebugobject.md) dargestellt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
