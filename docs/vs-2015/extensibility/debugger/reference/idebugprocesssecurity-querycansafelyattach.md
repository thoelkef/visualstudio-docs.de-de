---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft-Dokumentation
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
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187961"
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

- `S_OK`: Das Anfügen an Prozess sicher ist und kein Warnungsdialogfeld wird angezeigt.

- `S_FALSE`: Anfügen kann ein Sicherheitsproblem sein, und ein Dialogfeld mit einer Warnung angezeigt wird.

- `FAILURE`: Anhängen an Prozess ein Fehler auftritt.

## <a name="see-also"></a>Siehe auch
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)