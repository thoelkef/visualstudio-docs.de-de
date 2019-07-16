---
title: IDebugPortPicker::SetSite | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33d6d12bd21a6ab208fed019c1e0f763bce86724
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340350"
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

## <a name="parameters"></a>Parameter
`pSP`\
[in] Verweis auf die Schnittstelle des Dienstanbieters.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird aufgerufen werden, bevor Sie andere Methoden aufgerufen werden.

## <a name="see-also"></a>Siehe auch
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)