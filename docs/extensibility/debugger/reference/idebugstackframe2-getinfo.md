---
title: IDebugStackFrame2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09768fc58640d79a3b5628bafc16b2267f1f8a4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719724"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
Ruft eine Beschreibung des Stapelrahmens ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInfo ( 
   FRAMEINFO_FLAGS dwFieldSpec,
   UINT            nRadix,
   FRAMEINFO*      pFrameInfo
);
```

```csharp
int GetInfo ( 
   enum_FRAMEINFO_FLAGS dwFieldSpec,
   uint                 nRadix,
   FRAMEINFO[]          pFrameInfo
);
```

## <a name="parameters"></a>Parameter
`dwFieldSpec`\
[in] Eine Kombination von Flags aus der FRAMEINFO_FLAGS-Enumeration, die angibt, welche Felder des [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) `pFrameInfo` Parameters ausgefüllt werden sollen.

`nRadix`\
[in] Der Radix, der zum Formatieren numerischer Informationen verwendet werden soll.

`pFrameInfo`\
[out] Eine [FRAMEINFO-Struktur,](../../../extensibility/debugger/reference/frameinfo.md) die mit der Beschreibung des Stapelrahmens ausgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
