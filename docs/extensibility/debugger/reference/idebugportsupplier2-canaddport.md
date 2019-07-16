---
title: IDebugPortSupplier2::CanAddPort | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37f4fd246c376d08ab3ca006c543b44c4db2d73d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340294"
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