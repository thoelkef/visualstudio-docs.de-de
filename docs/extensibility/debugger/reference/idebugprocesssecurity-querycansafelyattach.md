---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44b125f44f3345e7bd28a9993a7a44be2e378b53
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701432"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Diese Methode ermöglicht Anschlusslieferanten um eine Warnung anzuzeigen, bevor der Benutzer fügt eine unsichere Prozess an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>Rückgabewert
 Die Rückgabewerte sind wie folgt aus:

-   `S_OK`: Das Anfügen an Prozess sicher ist und kein Warnungsdialogfeld wird angezeigt.

-   `S_FALSE`: Anfügen kann ein Sicherheitsproblem sein, und ein Dialogfeld mit einer Warnung angezeigt wird.

-   `FAILURE`: Anhängen an Prozess ein Fehler auftritt.

## <a name="see-also"></a>Siehe auch
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)