---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e03ccbb7761802401239768c54f4ea5b36ab86bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723197"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Diese Methode ermöglicht es dem Portlieferanten, eine Warnung anzuzeigen, bevor der Benutzer an einen unsicheren Prozess angefügt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Rückgabewert
 Die Rückgabewerte lauten wie folgt:

- `S_OK`: Das Anfügen an den Prozess ist sicher, und es wird kein Warndialogfeld angezeigt.

- `S_FALSE`: Das Anfügen kann ein Sicherheitsproblem darstellen, und es wird ein Dialogfeld mit einer Warnung angezeigt.

- `FAILURE`: Das Anfügen an den Prozess schlägt fehl.

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
