---
title: THUNK_ORDINAL | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b98098c0b6e1de9c3c2ceda5c644bc2957ab22bd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576407"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt Thunk-Typen fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum THUNK_ORDINAL {   
   THUNK_ORDINAL_NOTYPE,  
   THUNK_ORDINAL_ADJUSTOR,  
   THUNK_ORDINAL_VCALL,  
   THUNK_ORDINAL_PCODE,  
   THUNK_ORDINAL_LOAD   
  
   // trampoline thunk ordinals - only for use in Trampoline thunk symbols  
   THUNK_ORDINAL_TRAMP_INCREMENTAL,  
   THUNK_ORDINAL_TRAMP_BRANCHISLAND,  
} THUNK_ORDINAL;  
```  
  
## <a name="elements"></a>Elemente  
 THUNK_ORDINAL_NOTYPE  
 Standard-Thunk.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Ein- `this` oder-Thunk.  
  
 THUNK_ORDINAL_VCALL  
 Virtueller Rückruf.  
  
 THUNK_ORDINAL_PCODE  
 P-Code Thunk.  
  
 THUNK_ORDINAL_LOAD  
 Verzögert Lade Thunk.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Inkrementelles Trampolin Thunk (ein Trampolin-Thunk wird verwendet, um Aufrufe von einem Speicherplatz zu einem anderen zu überspringen).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Ein Zweig Punkt-Trampolin-Thunk.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) -Methode zurückgegeben.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
