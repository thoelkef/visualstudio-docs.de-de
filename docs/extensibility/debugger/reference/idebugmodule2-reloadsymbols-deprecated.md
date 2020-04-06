---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726919"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
VERALTET. NICHT VERWENDEN. Lädt die Symbole für dieses Modul neu.

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

## <a name="parameters"></a>Parameter
`pszUrlToSymbols`\
[in] Der Pfad zum Symbolspeicher.

`pbstrDebugMessage`\
[out] Gibt eine Informationsmeldung zurück, z. B. einen Status oder eine Fehlermeldung, die rechts neben dem Modulnamen im Fenster Module angezeigt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Ein Debugmodul sollte `E_FAIL`immer zurückgeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode wird nicht mehr unterstützt. Implementieren Sie stattdessen die [LoadSymbols-Methode.](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
