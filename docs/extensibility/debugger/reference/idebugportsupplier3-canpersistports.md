---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11bc6e21e8b70a5bd95c001f4173a7da3f3fe4be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340070"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Diese Methode bestimmt, ob die anschlusslieferant Ports gespeichert werden kann (indem sie auf den Datenträger geschrieben werden müssen) zwischen den Aufrufen des Debuggers.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 `S_OK` Wenn Ports beibehalten werden können, oder `S_FALSE` um anzugeben, dass die Ports nicht beibehalten werden können.

## <a name="remarks"></a>Hinweise
 Wenn Anschlusslieferanten Ports beibehalten kann, muss Sie tun, wenn es zerstört wird und Laden sie dann erneut, wenn er erneut instanziiert wird.

## <a name="see-also"></a>Siehe auch
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)