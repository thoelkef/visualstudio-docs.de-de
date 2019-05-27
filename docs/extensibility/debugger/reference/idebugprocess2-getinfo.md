---
title: IDebugProcess2::GetInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2970a4d2c65c56ab2e16ca51dbca6556bee1d040
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66202624"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
Ruft eine Beschreibung des Prozesses.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>Parameter
`Fields`\
[in] Eine Kombination von Werten aus der [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) Enumeration, der angibt, welche Felder von der `pProcessInfo` Parameter sind gefüllt werden soll.

`pProcessInfo`\
[out] Ein [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) -Struktur, die mit einer Beschreibung des Prozesses gefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)