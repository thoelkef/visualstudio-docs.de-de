---
title: "Ein Ausdruck vom Typ &#39;&lt;Typname&gt;&#39; kann nicht in „Object“ oder „ValueType“ konvertiert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31394"
  - "vbc31394"
helpviewer_keywords: 
  - "BC31394"
ms.assetid: e6f76257-65bb-4954-99f9-90f282648354
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein Ausdruck vom Typ &#39;&lt;Typname&gt;&#39; kann nicht in „Object“ oder „ValueType“ konvertiert werden.
Ein Ausdruck wird in einen Typ ausgewertet, der nicht von der Common Language Runtime \(CLR\) geschachtelt \(Boxing\) werden kann.  
  
 *Boxing* bezieht sich auf die Verarbeitung, die zum Konvertieren eines Typs in `Object` oder gelegentlich in <xref:System.ValueType> erforderlich ist. Die Common Language Runtime kann bestimmte Typen nicht schachteln, z. B. <xref:System.ArgIterator> und <xref:System.TypedReference>.  
  
 Wenn Sie `CType` oder `CObj` in der Anweisung nicht verwendet haben, die diesen Ausdruck enthält, dann hat [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] eine implizite Konvertierung versucht, die diesen Fehler verursacht.  
  
 **Fehler\-ID:** BC31394  
  
### So beheben Sie diesen Fehler  
  
1.  Suchen Sie den Ausdruck, der den angegebenen Typ ergibt.  
  
2.  Suchen Sie den Teil der Anweisung, in dem versucht wird, den genannten Typ zu schachteln.  
  
3.  Schreiben Sie die Anweisung neu, um die Boxing\-Konvertierung zu vermeiden.  
  
## Siehe auch  
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)