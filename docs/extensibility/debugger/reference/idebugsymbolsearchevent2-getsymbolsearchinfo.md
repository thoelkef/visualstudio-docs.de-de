---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d917a3f33d0c4339420c048fe20184245bb8dac1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868408"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Wird aufgerufen, von einem Ereignishandler, um Ergebnisse zu einem Symbol-Load-Prozess abzurufen.

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

#### <a name="parameters"></a>Parameter
 `pModule`

 [out] Ein IDebugModule3-Objekt, das das Modul für das die Symbole geladen wurden darstellt.

 `pbstrDebugMessage`

 [in, out] Gibt eine Zeichenfolge, die alle Fehlermeldungen aus dem Modul enthält. Wenn kein Fehler vorliegt, klicken Sie dann diese Zeichenfolge enthält nur den Modulnamen, aber sie ist niemals leer.

> [!NOTE]
> [C++] `pbstrDebugMessage` nicht `NULL` und freigegeben werden müssen, mit `SysFreeString`.

 `pdwModuleInfoFlags`

 [out] Eine Kombination von Flags aus der [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Enumeration, der angibt, ob keine Symbole geladen wurden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück.

## <a name="remarks"></a>Hinweise
 Wenn ein Ereignishandler empfängt die [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) Ereignis aus, nachdem versucht wird, um Debugsymbole für ein Modul zu laden, kann der Handler für diese Methode, um die Ergebnisse der diese Last zu ermitteln, aufrufen.

## <a name="see-also"></a>Siehe auch
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)