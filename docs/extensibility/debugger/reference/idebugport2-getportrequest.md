---
title: IDebugPort2::GetPortRequest | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48d39ea10e8425d5449444514489ac4b73c0a3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725334"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Ruft die Beschreibung eines Ports ab, der zuvor zum Erstellen des Ports verwendet wurde (sofern verfügbar).

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortRequest( 
   IDebugPortRequest2** ppRequest
);
```

```csharp
int GetPortRequest( 
   out IDebugPortRequest2 ppRequest
);
```

## <a name="parameters"></a>Parameter
`ppRequest`\
[out] Gibt ein [IDebugPortRequest2-Objekt](../../../extensibility/debugger/reference/idebugportrequest2.md) zurück, das die Anforderung darstellt, die zum Erstellen des Ports verwendet wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  Gibt `E_PORT_NO_REQUEST` zurück, wenn ein Port nicht mit einer [IDebugPortRequest2-Portanforderung](../../../extensibility/debugger/reference/idebugportrequest2.md) erstellt wurde.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
