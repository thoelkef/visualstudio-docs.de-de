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
ms.openlocfilehash: 6cd0b91491be365a4686265bd698717219df0afb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188404"
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