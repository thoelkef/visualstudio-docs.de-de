---
title: "&quot;System.Nullable&quot; erf&#252;llt die Structure-Einschr&#228;nkung f&#252;r den &lt;Typparametername&gt;-Typparameter nicht. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32115"
  - "vbc32115"
helpviewer_keywords: 
  - "BC32115"
ms.assetid: 98053645-fa76-4826-a7c1-f1bdf3511863
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;System.Nullable&quot; erf&#252;llt die Structure-Einschr&#228;nkung f&#252;r den &lt;Typparametername&gt;-Typparameter nicht.
Ein generischer Typ wird aufgerufen, indem ein Typargument vom Typ <xref:System.Nullable%601> an einen Typparameter mit einer `Structure`\-Einschränkung übergeben wird.  
  
 Die Common Language Runtime \(CLR\) lässt die <xref:System.Nullable%601>\-Struktur als Typargument für diese Struktur nicht zu. Obwohl es sich um eine Struktur handelt, die ansonsten die Anforderungen einer `Structure`\-Einschränkung erfüllt, könnte die rekursive Verwendung zu umständlichen Konstruktionen wie `Nullable(Of Nullable(Of Nullable))` führen.  
  
 **Fehler\-ID:** BC32115  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `Structure`\-Einschränkung aus dem Typparameter, oder ändern Sie das Typargument in einen anderen Werttyp als <xref:System.Nullable%601>.  
  
## Siehe auch  
 <xref:System.Nullable%601>   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)