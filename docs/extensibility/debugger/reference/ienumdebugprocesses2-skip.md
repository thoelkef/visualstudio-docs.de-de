---
title: IEnumDebugProzesse2::Überspringen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Skip
helpviewer_keywords:
- IEnumDebugProcesses2::Skip
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0e2cfee9c8cc0a8b2eecc745a29244016545ed3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715770"
---
# <a name="ienumdebugprocesses2skip"></a>IEnumDebugProcesses2::Skip
Überspringt die angegebene Anzahl von Elementen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parameter
`celt`\
[in] Anzahl der zu überspringenden Elemente.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` `celt` zurück, wenn die Anzahl der verbleibenden Elemente größer ist; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn `celt` ein Wert angegeben wird, der größer als die Anzahl der verbleibenden Elemente ist, wird die Enumeration auf das Ende festgelegt und `S_FALSE` zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
