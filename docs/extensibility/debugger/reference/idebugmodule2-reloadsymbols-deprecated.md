---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5651a85ccc89a8a084c608e3fc698aa326e07c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721302"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
VERALTET. VERWENDEN SIE NICHT. Lädt die Symbole für dieses Modul erneut.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

#### <a name="parameters"></a>Parameter
 `pszUrlToSymbols`

 [in] Der Pfad zu den Symbolspeicher.

 `pbstrDebugMessage`

 [out] Gibt eine informationsmeldung, z. B. eine Status- oder Fehlerinformationen Nachricht, die rechts neben den Namen des Moduls in das Fenster "Module" angezeigt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Eine Debug-Engine sollte immer zurückgeben `E_FAIL`.

## <a name="remarks"></a>Hinweise
 Diese Methode wird nicht mehr unterstützt. Implementieren der [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) Methode stattdessen.

## <a name="see-also"></a>Siehe auch
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)