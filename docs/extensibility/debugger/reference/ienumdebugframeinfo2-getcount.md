---
title: IEnumDebugFrameInfo2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2::GetCount
helpviewer_keywords:
- IEnumDebugFrameInfo2::GetCount
ms.assetid: d02a08e3-f34f-461e-8195-5157e154c481
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d319129d1869b90314c9c56960fc8d97fa09f9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716733"
---
# <a name="ienumdebugframeinfo2getcount"></a>IEnumDebugFrameInfo2::GetCount
Gibt die Anzahl der Elemente in der Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parameter
`pcelt`\
[out] Gibt die Anzahl der Elemente in der Enumeration zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode ist nicht Teil der üblichen COM-Enumerationsschnittstelle, `Skip`die `Reset` angibt, dass nur die `Next`, `Clone`, und Methoden implementiert werden müssen.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)
