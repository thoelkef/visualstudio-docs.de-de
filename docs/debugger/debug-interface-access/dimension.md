---
title: "Dimension | Microsoft Docs"
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
  - "Dimensionssymbol"
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Dimension
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Jedes Fortran\-Array verfügt über eine Dimension, die durch ein `SymTagDimension` Symbol identifiziert wird.  
  
## Eigenschaften  
 In der folgenden Tabelle sind die zusätzlichen gültige Eigenschaften für diesen Typ Symbol an.  
  
|Property|Datentyp|Beschreibung|  
|--------------|--------------|------------------|  
|[IDiaSymbol::get\_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|`IDiaSymbol*`|untere Grenze einer Fortran\-Arraydimension.|  
|[IDiaSymbol::get\_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|`DWORD`|ID des Symbols für das Untergrenze.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Index\-ID des Symbols.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Gibt `SymTagDimension` zurück \(einen der Werte [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md) \).|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|Obergrenze einer Fortran\-Arraydimension.|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|ID des Symbols für das obere Grenze.|  
  
## Siehe auch  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [Klassenhierarchie der Symboltypen](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)