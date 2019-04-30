---
title: IDebugPortSupplier2::CanAddPort | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19eb4d11ab6e67384a119f11bf070a27159c1676
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871828"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Stellt sicher, dass ein portanbieters neue Ports hinzufügen kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Rückgabewert
 Gibt zurück, wenn der Port hinzugefügt werden kann, `S_OK`ist, andernfalls gibt `S_FALSE` an, dass keine Ports können diese anschlusslieferant hinzugefügt werden.

## <a name="remarks"></a>Hinweise
 Rufen Sie diese Methode vor dem Aufruf der [Port hinzufügen](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) Methode, da die zweite Methode erstellt, den Port sowie das Hinzufügen, die möglicherweise einen zeitaufwändigen Vorgang.

## <a name="see-also"></a>Siehe auch
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)