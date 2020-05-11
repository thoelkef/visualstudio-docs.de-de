---
title: IDebugMemoryContext2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c190710afc9231662fa12c5552d6f73e0268b643
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727461"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
Ruft eine [CONTEXT_INFO-Struktur](../../../extensibility/debugger/reference/context-info.md) ab, die den Kontext beschreibt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInfo( 
   CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO*       pInfo
);
```

```csharp
int GetInfo(
   enum_CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO[]           pinfo
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
[in] Eine Kombination von Flags aus der CONTEXT_INFO_FIELDS-Enumeration, die angeben, welche Felder der [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur ausgefüllt werden sollen. [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)

`pInfo`\
[in, out] Die `CONTEXT_INFO` Ausgefüllte Struktur.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
