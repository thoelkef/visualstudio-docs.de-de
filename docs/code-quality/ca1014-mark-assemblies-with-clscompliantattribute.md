---
title: "CA1014: Assemblys mit CLSCompliantAttribute markieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014: Assemblys mit CLSCompliantAttribute markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Auf eine Assembly wird das <xref:System.CLSCompliantAttribute?displayProperty=fullName>\-Attribut nicht angewendet.  
  
## Regelbeschreibung  
 In der Common Language Specification \(CLS\) sind Benennungseinschränkungen, Datentypen und Regeln definiert, denen Assemblys entsprechen müssen, wenn sie in verschiedenen Programmiersprachen verwendet werden sollen.  Um guten Entwurfsprinzipien gerecht zu werden, muss bei allen Assemblys die CLS\-Kompatibilität mit <xref:System.CLSCompliantAttribute> explizit angegeben werden.  Wenn das Attribut in einer Assembly nicht vorhanden ist, ist die Assembly nicht kompatibel.  
  
 Eine CLS\-kompatible Assembly kann Typen oder Typmember enthalten, die nicht kompatibel sind.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Assembly das Attribut hinzu.  Anstatt die gesamte Assembly als nicht kompatible Assembly zu definieren, sollten Sie feststellen, welcher Typ oder welche Typmember nicht kompatibel sind, und diese Elemente entsprechend kennzeichnen.  Nach Möglichkeit sollten Sie eine CLS\-kompatible Alternative für nicht kompatible Member bereitstellen, damit möglichst viele Benutzer auf die Funktionen der Assembly zugreifen können.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Wenn die Assembly nicht kompatibel sein soll, wenden Sie das Attribut an, und legen Sie seinen Wert auf `false` fest.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Assembly mit dem <xref:System.CLSCompliantAttribute?displayProperty=fullName>\-Attribut, das die Assembly als CLS\-kompatibel deklariert.  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## Siehe auch  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)