---
title: Konstanten (Debug Interface Access SDK) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff1b473f7e5fdddbb1706d54e44692df3a6022e2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513154"
---
# <a name="constants-debug-interface-access-sdk"></a>Konstanten (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Konstanten (Debug Interface Access SDK)](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/constants-debug-interface-access-sdk).  
  
Diese Zeichenfolgenkonstanten können zum Identifizieren der verschiedenen Abschnitte der ein Programm debuggen Programmdatenbankdatei (PDB) an, über das DIA-SDK verwendet werden.  
  
## <a name="constants"></a>Konstanten  
 Im folgenden werden als C/C++-Makros deklariert.  
  
|Makro|Wert|  
|-----------|-----------|  
|`DiaTable_Symbols`|L "Symbole"|  
|`DiaTable_Sections`|L "Abschnitte"|  
|`DiaTable_SrcFiles`|L "SourceFiles"|  
|`DiaTable_LineNums`|L "LineNumbers"|  
|`DiaTable_SegMap`|L "SegmentMap"|  
|`DiaTable_Dbg`|L "Dbg"|  
|`DiaTable_InjSrc`|L "InjectedSource"|  
|`DiaTable_FrameData`|L "FrameData"|  
  
## <a name="example"></a>Beispiel  
 Hier ist ein Beispiel mit einer der folgenden Symbole:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Referenz](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)



