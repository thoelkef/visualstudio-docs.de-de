---
title: IDebugObject2::IsEncOutdated | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ca5b4818f66363159dacf950766c6104aab4a34
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209809"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Diese Methode bestimmt, ob der Bearbeiten und Fortfahren-Status dieses Objekts oder des übergeordneten Containers veraltet ist. Diese Methode und gibt immer eine benutzerdefinierte ausdrucksauswertung nicht implementiert `E_NOTIMPL`.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Parameter
`pfEncOutdated`\
[out] Ungleich Null (`TRUE`), wenn der Bearbeiten und Fortfahren-Status nicht mehr aktuell ist, NULL (`FALSE`) ist dies nicht.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

> [!NOTE]
> Eine benutzerdefinierte ausdrucksauswertung sollte immer zurückgeben `E_NOTIMPL`.

## <a name="see-also"></a>Siehe auch
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)