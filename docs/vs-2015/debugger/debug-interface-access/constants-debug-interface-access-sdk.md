---
title: Konstanten (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 931e1ab46793a5ff7e0434949330eaf4dbc820e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164427"
---
# <a name="constants-debug-interface-access-sdk"></a>Konstanten (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Diese Zeichen folgen Konstanten können verwendet werden, um verschiedene Abschnitte einer Programm-Debug-Datenbankdatei (PDB-Datei) über die Dia SDK zu identifizieren.  
  
## <a name="constants"></a>Konstanten  
 Folgendes wird als C/C++-Makros deklariert.  
  
|Makro|Wert|  
|-----------|-----------|  
|`DiaTable_Symbols`|L "Symbole"|  
|`DiaTable_Sections`|L "Abschnitte"|  
|`DiaTable_SrcFiles`|L"SourceFiles"|  
|`DiaTable_LineNums`|L"LineNumbers"|  
|`DiaTable_SegMap`|L"SegmentMap"|  
|`DiaTable_Dbg`|L"Dbg"|  
|`DiaTable_InjSrc`|L "injetedsource"|  
|`DiaTable_FrameData`|L"FrameData"|  
  
## <a name="example"></a>Beispiel  
 Im folgenden finden Sie ein Beispiel für die Verwendung eines der folgenden Symbole:  
  
```cpp#  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Angabe](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
