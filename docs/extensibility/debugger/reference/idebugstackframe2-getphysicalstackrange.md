---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719669"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Ruft eine maschinenabhängige Darstellung des Bereichs physischer Adressen ab, die einem Stapelrahmen zugeordnet sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>Parameter
`paddrMin`\
[out] Gibt die niedrigste physische Adresse zurück, die diesem Stapelrahmen zugeordnet ist.

`paddrMax`\
[out] Gibt die höchste physische Adresse zurück, die diesem Stapelrahmen zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die von dieser Methode zurückgegebenen Informationen werden vom Sitzungsdebug-Manager (SDM) zum Sortieren von Stackframes verwendet.

 Es wird davon ausgegangen, dass die Aufrufliste nach unten wächst, d. h., dass neue Stapelrahmen an immer niedrigeren Speicheradressen hinzugefügt werden. Eine Laufzeitarchitektur muss physische Stapelbereiche bereitstellen, die dieser Annahme entsprechen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
