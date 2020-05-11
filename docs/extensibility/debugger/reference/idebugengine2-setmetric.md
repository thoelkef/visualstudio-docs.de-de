---
title: IDebugEngine2::SetMetric | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: caada8db1791d94e7a9632394cd4659bf8cec3a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730896"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Diese Methode legt einen Registrierungswert fest, der als Metrik bezeichnet wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parameter
`pszMetric`\
[in] Der Metrikname.

`varValue`\
[in] Gibt den Metrikwert an.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Eine Metrik ist ein Registrierungswert, der verwendet wird, um das Verhalten eines Debugmoduls zu ändern oder unterstützte Funktionen anzukündigen. Diese Methode kann den Aufruf an die entsprechende Form der `SetMetric` [SDK-Hilfsfunktion für](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) das Debuggen weiterleiten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [SDK-Hilfsprogramme für das Debuggen](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
