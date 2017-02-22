---
title: "THUNK_ORDINAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Thunk_Ordinal-Enumeration"
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# THUNK_ORDINAL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt Thunk Typen festgelegt.  
  
## Syntax  
  
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
  
## Elements  
 THUNK\_ORDINAL\_NOTYPE  
 Standardwert thunk.  
  
 THUNK\_ORDINAL\_ADJUSTOR  
 Ein `this`\-Steuerelement thunk.  
  
 THUNK\_ORDINAL\_VCALL  
 Verbindungsanforderungsthunk.  
  
 THUNK\_ORDINAL\_PCODE  
 P\-Code Thunk.  
  
 THUNK\_ORDINAL\_LOAD  
 Verzögern thunk laden.  
  
 THUNK\_ORDINAL\_TRAMP\_INCREMENTAL  
 Inkrementeller Trampoline thunk \(ein Trampoline thunk wird verwendet, um Aufrufe von einem Speicherbereich zu einem anderen zu wechseln.\)  
  
 THUNK\_ORDINAL\_TRAMP\_BRANCHISLAND  
 Verzweigungspunkt\-Trampolinethunk.  
  
## Hinweise  
 Die Werte in dieser Enumeration werden von einem Aufruf der [IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)\-Methode zurückgegeben.  
  
## Anforderungen  
 Header: cvconst.h  
  
## Siehe auch  
 [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)