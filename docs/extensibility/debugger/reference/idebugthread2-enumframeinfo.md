---
title: IDebugThread2::EnumFrameInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bd3c6d46a577930cc7a2b87c85cd82a55f8cf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718864"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
Ruft eine Liste der Stapelrahmen für diesen Thread ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumFrameInfo ( 
   FRAMEINFO_FLAGS        dwFieldSpec,
   UINT                   nRadix,
   IEnumDebugFrameInfo2** ppEnum
);
```

```csharp
int EnumFrameInfo ( 
   enum_FRAMEINFO_FLAGS     dwFieldSpec,
   uint                     nRadix,
   out IEnumDebugFrameInfo2 ppEnum
);
```

## <a name="parameters"></a>Parameter
`dwFieldSpec`\
[in] Eine Kombination von [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) Flags aus der FRAMEINFO_FLAGS-Enumeration, die angibt, welche Felder der [FRAMEINFO-Strukturen](../../../extensibility/debugger/reference/frameinfo.md) ausgefüllt werden sollen. Geben `FIF_FUNCNAME_FORMAT` Sie das Flag an, um den Funktionsnamen in eine einzelne Zeichenfolge zu formatieren.

`nRadix`\
[in] Radix, das zum Formatieren numerischer Informationen im Enumerator verwendet wird.

`ppEnum`\
[out] Gibt ein [IEnumDebugFrameInfo2-Objekt](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) zurück, das eine Liste von [FRAMEINFO-Strukturen](../../../extensibility/debugger/reference/frameinfo.md) enthält, die den Stapelrahmen beschreiben.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Rahmen des Threads werden in der Reihenfolge aufgezählt, wobei der aktuelle Rahmen zuerst und der älteste Frame zuletzt aufgezählt werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
