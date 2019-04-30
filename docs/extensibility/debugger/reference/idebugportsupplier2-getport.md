---
title: IDebugPortSupplier2::GetPort | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65b2d8264ef75c46de32ee65d994794d526c7ddb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871421"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Ruft einen Port aus eines portanbieters ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

#### <a name="parameters"></a>Parameter
 `guidPort`

 [in] Global eindeutiger Bezeichner (GUID) des Ports.

 `ppPort`

 [out] Gibt eine [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) Objekt, das den Port darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_PORTSUPPLIER_NO_PORT` Wenn kein Port mit der angegebenen ID vorhanden ist.

## <a name="see-also"></a>Siehe auch
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)