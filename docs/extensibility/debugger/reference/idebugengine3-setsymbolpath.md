---
title: IDebugEngine3::SetSymbolPath | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: da2318e9e2e30ea4cf0dce4bef6abd03aef2b0d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352475"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Legt fest, den Pfad oder die Pfade, die für das Debuggen von Symbolen durchsucht werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>Parameter

`szSymbolSearchPath`\
[in] Eine Zeichenfolge mit den Symbolsuchpfad oder die Pfade. Einzelheiten finden Sie unter "Hinweise". Darf nicht NULL sein.

`szSymbolCachePath`\
[in] Eine Zeichenfolge mit den lokalen Pfad, in dem Symbole zwischengespeichert werden können. Darf nicht NULL sein.

`Flags`\
[in] Nicht verwendet. immer auf 0 festgelegt.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Zeichenfolge `szSymbolSearchPath` ist eine Liste von einem oder mehreren Pfaden, getrennt durch ein Semikolon nach Symbolen sucht. Diese Pfade können es sich um einen lokalen Pfad, einen UNC-Format-Pfad oder eine URL sein. Diese Pfade können auch eine Mischung verschiedener Domänentypen sein. Wenn der Pfad UNC ist (z. B. \\\Symserver\Symbols), und klicken Sie dann die Debug-Engine bestimmt werden soll, wenn der Pfad auf einem Symbolserver und sollte in der Lage, laden Symbole von diesem Server, und speichern Sie sie in der Pfadangabe von `szSymbolCachePath`.

 Der Symbolpfad kann auch eine oder mehrere cachespeicherorte enthalten. Caches sind in der Reihenfolge ihrer Priorität, mit der höchsten Priorität Cache zuerst aufgeführt und getrennt von * Symbole. Zum Beispiel:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com
```

 Die [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) Methode führt die tatsächliche Last der Symbole.

## <a name="see-also"></a>Siehe auch
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)