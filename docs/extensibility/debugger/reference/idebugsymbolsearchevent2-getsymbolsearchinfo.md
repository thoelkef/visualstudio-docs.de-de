---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718886"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Wird von einem Ereignishandler aufgerufen, um Ergebnisse über einen Symbolladeprozess abzurufen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Parameter
`pModule`\
[out] Ein IDebugModule3-Objekt, das das Modul darstellt, für das die Symbole geladen wurden.

`pbstrDebugMessage`\
[in, out] Gibt eine Zeichenfolge zurück, die Fehlermeldungen aus dem Modul enthält. Wenn kein Fehler auftritt, enthält diese Zeichenfolge nur den Namen des Moduls, aber sie ist nie leer.

> [!NOTE]
> [C++] `pbstrDebugMessage` kann `NULL` nicht mit freigegeben `SysFreeString`werden und muss mit freigegeben werden.

`pdwModuleInfoFlags`\
[out] Eine Kombination von [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Flags aus der MODULE_INFO_FLAGS-Enumeration an, die angibt, ob Symbole geladen wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn ein Handler das [IDebugSymbolSearchEvent2-Ereignis](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) empfängt, nachdem versucht wurde, Debugsymbole für ein Modul zu laden, kann der Handler diese Methode aufrufen, um die Ergebnisse dieser Last zu ermitteln.

## <a name="see-also"></a>Weitere Informationen
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
