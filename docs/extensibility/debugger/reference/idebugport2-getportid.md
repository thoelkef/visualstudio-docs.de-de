---
title: IDebugPort2::GetPortId | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2::GetPortId
helpviewer_keywords:
- IDebugPort2::GetPortId
ms.assetid: 837cb924-c113-4224-aa86-3e02b33dfa70
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ed27e5bc70a26c19784b3b543da791fdf1ff0bd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685624"
---
# <a name="idebugport2getportid"></a>IDebugPort2::GetPortId
Ruft die Port-ID ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPortId( 
   GUID* pguidPort
);
```

```csharp
int GetPortId( 
   out Guid pguidPort
);
```

#### <a name="parameters"></a>Parameter
 `pguidPort`

 [out] Gibt die GUID zurück, der den Port identifiziert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)