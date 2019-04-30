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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576407"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Legt fest, Thunk-Typen.  
  
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
  
## <a name="elements"></a>Elements  
 THUNK_ORDINAL_NOTYPE  
 Standard-Thunk.  
  
 THUNK_ORDINAL_ADJUSTOR  
 Ein `this` Abwicklung Thunk.  
  
 THUNK_ORDINAL_VCALL  
 Virtueller Aufruf Thunk.  
  
 THUNK_ORDINAL_PCODE  
 Thunk für P-Code.  
  
 THUNK_ORDINAL_LOAD  
 Verzögert Thunk.  
  
 THUNK_ORDINAL_TRAMP_INCREMENTAL  
 Inkrementelle Trampoline-Thunk (ein Thunk Trampoline wird verwendet, um die Aufrufe aus einem Speicher in einen anderen zu springen).  
  
 THUNK_ORDINAL_TRAMP_BRANCHISLAND  
 Branch Punkt Trampoline Thunk.  
  
## <a name="remarks"></a>Hinweise  
 Die Werte in dieser Enumeration werden zurückgegeben, von einem Aufruf der [idiasymbol:: Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: cvconst.h  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
