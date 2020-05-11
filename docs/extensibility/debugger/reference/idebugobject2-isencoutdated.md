---
title: IDebugObject2::IsEncVeraltet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90ff97b87ec2abaab87dfece5b2a2ac1cabb28c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726105"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Diese Methode bestimmt, ob der Status Bearbeiten und Fortsetzen dieses Objekts oder des übergeordneten Containers veraltet ist. Ein benutzerdefinierter Ausdrucksauswertungswert implementiert diese `E_NOTIMPL`Methode nicht und gibt immer zurück.

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
[out] Ein Wert`TRUE`ungleich Null ( ), wenn der`FALSE`Status Bearbeiten und Fortsetzen veraltet ist, Null ( ), wenn dies nicht der Fall ist.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

> [!NOTE]
> Ein benutzerdefinierter Ausdrucksauswertungswert sollte immer zurückgeben. `E_NOTIMPL`

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
