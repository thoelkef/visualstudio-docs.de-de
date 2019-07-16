---
title: IDebugProcessSecurity::GetUserName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a42b67eb3fd308011bf725f8dd7e24a4d9ddca6f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311524"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Ruft den Benutzernamen aus den Anschlusslieferanten ab.

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
[out] Eine Zeichenfolge mit den Benutzernamen ein.

## <a name="return-value"></a>Rückgabewert
 Wenn die Methode erfolgreich ist, gibt es `S_OK`. Andernfalls wird einen Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 `GetUserName` Gibt den Benutzernamen zurück, die in angezeigt wird der **Benutzernamen** Spalte die **an den Prozess anhängen** Dialogfeld. Anzeigen der **an den Prozess anhängen** Dialogfeld klicken Sie auf **an den Prozess anhängen** auf die **Tools** im Menü der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE).

## <a name="see-also"></a>Siehe auch
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)