---
title: Konstanten (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a120a1610e6ca62ba4c19bb5dd2289628e1d273
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987404"
---
# <a name="constants-debug-interface-access-sdk"></a>Konstanten (Debug Interface Access SDK)
Diese Zeichenfolgenkonstanten können zum Identifizieren der verschiedenen Abschnitte der ein Programm debuggen Programmdatenbankdatei (PDB) an, über das DIA-SDK verwendet werden.

## <a name="constants"></a>Konstanten
Im folgenden werden als C/C++-Makros deklariert.

|Makro|Wert|
|-----------|-----------|
|`DiaTable_Symbols`|L "Symbole"|
|`DiaTable_Sections`|L "Abschnitte"|
|`DiaTable_SrcFiles`|L"SourceFiles"|
|`DiaTable_LineNums`|L"LineNumbers"|
|`DiaTable_SegMap`|L"SegmentMap"|
|`DiaTable_Dbg`|L"Dbg"|
|`DiaTable_InjSrc`|L "InjectedSource"|
|`DiaTable_FrameData`|L"FrameData"|

## <a name="example"></a>Beispiel
Hier ist ein Beispiel mit einer der folgenden Symbole:

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>Anforderungen
Header: dia2.h

## <a name="see-also"></a>Siehe auch
[Verweis](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
[Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
