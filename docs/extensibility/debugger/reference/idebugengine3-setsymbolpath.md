---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730662"
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
[in] Zeichenfolge, die den Symbolsuchpfad oder die Pfade enthält. Weitere Informationen finden Sie unter "Bemerkungen". Lässt keine NULL-Werte zu.

`szSymbolCachePath`\
[in] Zeichenfolge, die den lokalen Pfad enthält, in dem Symbole zwischengespeichert werden können. Lässt keine NULL-Werte zu.

`Flags`\
[in] Nicht verwendet; immer auf 0 gesetzt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die `szSymbolSearchPath` Zeichenfolge ist eine Liste von einem oder mehreren Pfaden, die durch Semikolons getrennt sind, um nach Symbolen zu suchen. Bei diesen Pfaden kann es sich um einen lokalen Pfad, einen UNC-Pfad oder eine URL handelt. Diese Pfade können auch eine Mischung aus verschiedenen Typen sein. Wenn der Pfad UNC ist \\(z. B. "Symserver"-Symbole), sollte das Debugmodul bestimmen, ob der Pfad zu einem Symbolserver `szSymbolCachePath`erfolgt, und sollte in der Lage sein, Symbole von diesem Server zu laden, indem es sie in dem von angegebenen Pfad zwischenspeichern kann.

 Der Symbolpfad kann auch einen oder mehrere Cachespeicherorte enthalten. Caches werden in der Prioritätsreihenfolge mit der höchsten Priorität Cache zuerst aufgelistet und durch * Symbole getrennt. Beispiel:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Die [LoadSymbols-Methode](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) führt die tatsächliche Last der Symbole aus.

## <a name="see-also"></a>Weitere Informationen
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
