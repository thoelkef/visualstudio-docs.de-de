---
title: 'Idebugprocesssecurity:: querycansafelyattach | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723197"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Mit dieser Methode kann der Port Lieferant eine Warnung anzeigen, bevor der Benutzer an einen unsicheren Prozess angefügt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Rückgabewert
 Die Rückgabewerte lauten wie folgt:

- `S_OK`: Das Anhängen an den Prozess ist sicher, und es wird kein Warn Dialogfeld angezeigt.

- `S_FALSE`: Das Anfügen kann ein Sicherheitsproblem sein, und es wird ein Dialogfeld mit einer Warnung angezeigt.

- `FAILURE`: Fehler beim Anhängen an den Prozess.

## <a name="see-also"></a>Siehe auch
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
