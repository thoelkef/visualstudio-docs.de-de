---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730682"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Diese Methode informiert das Debugmodul über die JustMyCode-Statusinformationen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>Parameter
`fUpdate`\
[in] Ein Wert`TRUE`ungleich Null (`FALSE`), um aktuelle Informationen zu aktualisieren, Null ( ), um alle Informationen zurückzusetzen (wobei alles zuvor festgelegte verwendet wird).

`dwModules`\
[in] Anzahl der Informationsstrukturen in`rgJMCSpec.`

`rgJMCSpec`\
[in] Array von [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) zu verwendenden Strukturen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 JustMyCode ist das Konzept, nur den Code zu debuggen, der einem Benutzer gehört, und den gesamten Zwischencode wie Systemcode zu ignorieren – auch wenn Quellcode für diesen Systemcode verfügbar ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
