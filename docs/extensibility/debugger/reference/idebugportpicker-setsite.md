---
title: IDebugPortPicker::SetSite | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0964c94334ca0815b4410f6858dca5502b2f8a1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678461"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Legt den Dienstanbieter fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

#### <a name="parameters"></a>Parameter
 `pSP`

 [in] Verweis auf die Schnittstelle des Dienstanbieters.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird aufgerufen werden, bevor Sie andere Methoden aufgerufen werden.

## <a name="see-also"></a>Siehe auch
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)