---
title: IDebugPort2::GetPortRequest | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8a103316a292c444a35b8c819968d98cda777b6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678123"
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Ruft die Beschreibung eines Ports, die zuvor verwendet wurde, um den Port (falls verfügbar) zu erstellen.

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

#### <a name="parameters"></a>Parameter
 `ppRequest`

 [out] Gibt eine [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) Objekt, das die Anforderung, die verwendet wurde, erstellen Sie den Port darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  Gibt `E_PORT_NO_REQUEST` Wenn mit ein Port nicht erstellt wurde ein [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) Port-Anforderung.

## <a name="see-also"></a>Siehe auch
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)