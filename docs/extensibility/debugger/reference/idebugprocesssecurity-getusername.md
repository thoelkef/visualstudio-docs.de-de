---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723259"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Ruft den Benutzernamen vom Portlieferanten ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Parameter
`pbstrUserName`\
[out] Eine Zeichenfolge, die den Benutzernamen enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn die Methode erfolgreich ist, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 `GetUserName`gibt den Benutzernamen zurück, der in der Spalte **Benutzername** des Dialogfelds **An Prozess anfügen** angezeigt wird. Um das Dialogfeld **An Prozess anfügen** anzuzeigen, klicken [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Sie im Menü **Extras** in der integrierten Entwicklungsumgebung (IDE) auf An Prozess **anfügen.**

## <a name="see-also"></a>Weitere Informationen
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
