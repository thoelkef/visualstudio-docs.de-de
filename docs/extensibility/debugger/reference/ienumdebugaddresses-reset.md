---
title: IEnumDebugAddresses::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 48026ee5f359c80c2c807fa857f1ec749823e2b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717624"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
Diese Methode setzt die Enumeration auf das erste Element zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Nachdem diese Methode aufgerufen wurde, gibt der nächste Aufruf von [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) das erste Element der Enumeration zurück.

## <a name="see-also"></a>Weitere Informationen
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [Weiter](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
