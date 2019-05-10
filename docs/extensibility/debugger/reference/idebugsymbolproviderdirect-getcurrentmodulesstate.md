---
title: IDebugSymbolProviderDirect::GetCurrentModulesState | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4db91b1495484adff076e959021b4791f1e62a29
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458225"
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