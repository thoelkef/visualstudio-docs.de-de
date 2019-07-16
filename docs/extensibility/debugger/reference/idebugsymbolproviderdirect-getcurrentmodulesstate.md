---
title: IDebugSymbolProviderDirect::GetCurrentModulesState | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59f1917f420e4815bcd525f131e4b524e53e6b3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347316"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
Ruft Informationen über die Symbol-Gruppe, die Mitglied der symbolanbieter ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCurrentModulesState(
    DWORD*          pState,
    unsigned long * count
);
```

```csharp
int GetCurrentModulesState(
    out uint pState,
    out uint count
);
```

## <a name="parameters"></a>Parameter
`pState`\
[out] Der Status der Gruppe der Symbol-Anbieter.

`count`\
[out] Die Anzahl der Module in der Gruppe.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Status wird geändert, wenn ein Modul hinzugefügt oder aus, der Symbol-Gruppe entfernt wird. Aus diesem Grund kann diese Methode verwendet werden, um festzustellen, ob eine Symbol-Gruppe geändert wurde.

## <a name="see-also"></a>Siehe auch
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)