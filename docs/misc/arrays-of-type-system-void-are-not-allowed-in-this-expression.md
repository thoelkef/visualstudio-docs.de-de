---
title: "Arrays vom Typ &#39;System.Void&#39; sind in diesem Ausdruck nicht zul&#228;ssig | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31428"
  - "bc31428"
helpviewer_keywords: 
  - "BC31428"
ms.assetid: 21d77b56-585f-4107-b7ec-21933ba58017
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arrays vom Typ &#39;System.Void&#39; sind in diesem Ausdruck nicht zul&#228;ssig
Ein Ausdruck in einer Zuweisungsanweisung oder einer Deklaration gibt ein Array vom Typ <xref:System.Void> an.  
  
 Die <xref:System.Void>\-Struktur ist ein spezieller Typ, der intern von .NET Framework und insbesondere von Visual C\# und Visual C\+\+ verwendet wird. Die Struktur stellt einen Rückgabewerttyp für eine Methode dar, die keinen Wert zurückgibt. Visual Basic verwendet eine `Sub`\-Prozedur, wenn kein Wert zurückgegeben wird, und eine `Function`\-Prozedur, wenn ein Wert zurückgegeben wird.  
  
 Arrays des Typs <xref:System.Void> sind ohne Bedeutung und sind in jedem Kontext unzulässig.  
  
 **Fehler\-ID:** BC31428  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Klammern, die ein Array angeben.  
  
2.  Sofern es keinen bestimmten Grund gibt, einen Laufzeittyp mit <xref:System.Void> zu vergleichen, sollten Sie den Verweis darauf vollständig entfernen.  
  
## Siehe auch  
 <xref:System.Void>