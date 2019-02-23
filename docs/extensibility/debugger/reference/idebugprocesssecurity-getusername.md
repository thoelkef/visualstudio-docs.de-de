---
title: IDebugProcessSecurity::GetUserName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8340e9fd9e5f38963a9de78e2974404f600deef
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686170"
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

#### <a name="parameters"></a>Parameter
 `pbstrUserName`

 [out] Eine Zeichenfolge mit den Benutzernamen ein.

## <a name="return-value"></a>Rückgabewert
 Wenn die Methode erfolgreich ist, gibt es `S_OK`. Andernfalls wird einen Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 `GetUserName` Gibt den Benutzernamen zurück, die in angezeigt wird der **Benutzernamen** Spalte die **an den Prozess anhängen** Dialogfeld. Anzeigen der **an den Prozess anhängen** Dialogfeld klicken Sie auf **an den Prozess anhängen** auf die **Tools** im Menü der [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE).

## <a name="see-also"></a>Siehe auch
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)