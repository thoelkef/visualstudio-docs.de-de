---
title: "CA1011: Basistypen als Parameter &#252;bergeben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1011: Basistypen als Parameter &#252;bergeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methodendeklaration enthält einen formalen Parameter, der ein abgeleiteter Typ ist, und die Methode ruft nur Member des Basistyps des Parameters auf.  
  
## Regelbeschreibung  
 Wenn in einer Methodendeklaration ein Basistyp als Parameter angegeben wird, kann jeder Typ, der von diesem Basistyp abgeleitet ist, als entsprechendes Argument an die Methode übergeben werden.  Wenn das Argument innerhalb der Methode verwendet wird, dann hängt es vom Typ des Arguments ab, welche Methode ausgeführt wird.  Wenn die vom abgeleiteten Typ bereitgestellte zusätzliche Funktionalität nicht erforderlich ist, lässt die Verwendung des Basistyps eine allgemeinere Nutzung der Methode zu.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Typ des Parameters in seinen Basistyp.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden.  
  
-   wenn die Methode die bestimmte Funktionalität erfordert, die vom abgeleiteten Typ bereitgestellt wird  
  
     – oder –  
  
-   um zu erzwingen, dass nur der abgeleitete Typ oder ein weiter abgeleiteter Typ an die Methode übergeben wird.  
  
 In diesen Fällen ist der Code wegen der starken Typüberprüfung, die Compiler und Laufzeitbibliothek bereitstellen, robuster.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode mit dem Namen `ManipulateFileStream` veranschaulicht, die nur mit einem <xref:System.IO.FileStream>\-Objekt verwendet werden kann, was gegen diese Regel verstößt.  Bei einer zweiten Methode mit dem Namen `ManipulateAnyStream` wird der <xref:System.IO.FileStream>\-Parameter durch einen <xref:System.IO.Stream>\-Parameter ersetzt und die Regel somit eingehalten.  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## Verwandte Regeln  
 [CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)