---
title: 'IDebugEngine3:: setsymbolpath | Microsoft-Dokumentation'
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
ms.openlocfilehash: 0fe3000804971c8bd8cbf896a592bd11b875bfa8
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506388"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Legt den Pfad oder die Pfade fest, die nach Debugsymbolen durchsucht werden.

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
in Zeichenfolge, die den Pfad oder die Pfade der Symbol Suche enthält. Weitere Informationen finden Sie unter "Hinweise". Lässt keine NULL-Werte zu.

`szSymbolCachePath`\
in Zeichenfolge, die den lokalen Pfad enthält, in dem Symbole zwischengespeichert werden können Lässt keine NULL-Werte zu.

`Flags`\
in Nicht verwendet; immer auf 0 festgelegt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Zeichenfolge `szSymbolSearchPath` ist eine Liste mit einem oder mehreren durch Semikolons getrennten Pfaden, um nach Symbolen zu suchen. Diese Pfade können ein lokaler Pfad, ein UNC-Pfad oder eine URL sein. Diese Pfade können auch eine Mischung verschiedener Typen sein. Wenn der Pfad UNC ist (z. b. \\\symserver\symbols), sollte die Debug-Engine bestimmen, ob der Pfad zu einem Symbol Server ist, und dass Sie in der Lage sein soll, Symbole von diesem Server zu laden und diese im durch `szSymbolCachePath`angegebenen Pfad zwischenzuspeichern.

 Der Symbol Pfad kann auch einen oder mehrere Cache Speicherorte enthalten. Caches werden in der Prioritäts Reihenfolge aufgelistet, wobei der Cache mit der höchsten Priorität zuerst und durch * Symbole getrennt ist. Beispiel:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Die [loadsymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) -Methode führt die tatsächliche Auslastung der Symbole aus.

## <a name="see-also"></a>Weitere Informationen
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)