---
title: IDebugModuleLoadEvent2::GetModule | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6ee91686051440fe44efd1f4e4f9ba933f3e0c99
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323699"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Ruft das Modul, das gerade geladen oder entladen wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>Parameter
`pModule`\
[out] Gibt eine [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Objekt, das das Modul darstellt, die geladen oder entladen wird.

`pbstrDebugMessage`\
[in, out] Gibt eine optionale Nachricht, die dieses Ereignis beschreibt. Wenn dieser Parameter ein null-Wert ist, wird keine Meldung angefordert.

`pbLoad`\
[in, out] Ungleich Null (`TRUE`) Wenn das Modul geladen und 0 (null) ist (`FALSE`), wenn das Modul entladen wird. Wenn dieser Parameter ein null-Wert ist, wird kein Status angefordert.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)