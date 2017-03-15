---
title: "Der Name &#39;&lt;Name&gt;&#39; ist entweder nicht deklariert oder im aktuellen Bereich ung&#252;ltig. | Microsoft Docs"
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
  - "vbc36610"
  - "bc36610"
helpviewer_keywords: 
  - "BC36610"
ms.assetid: e66a4b8a-9252-42ae-a30d-341fad4f74be
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Name &#39;&lt;Name&gt;&#39; ist entweder nicht deklariert oder im aktuellen Bereich ung&#252;ltig.
Eine LINQ\-Abfrage bezieht sich auf ein Programmierelement, aber der Compiler kann kein Element mit genau diesem Namen finden.  
  
 **Fehler\-ID:** BC36610  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise des Namens in der verweisenden Anweisung. Bei [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] wird die Groß\-\/Kleinschreibung berücksichtigt, aber eine andere Variante der Schreibweise bildet einen anderen Namen. Beachten Sie, dass der Unterstrich \(`_`\) Teil des Namens und daher Teil der Schreibweise ist.  
  
2.  Überprüfen Sie, ob sich das Programmierelement im Gültigkeitsbereich befindet. Wenn die verweisende Anweisung außerhalb des Bereichs liegt, der das Programmierelement deklariert, müssen Sie den Elementnamen möglicherweise qualifizieren. Weitere Informationen finden Sie unter [Scope in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/scope).  
  
3.  Stellen Sie sicher, dass Sie den Memberzugriffsoperator \(`.`\) zwischen einem Objekt und seinem Member verwenden. Wenn Sie z. B. ein <xref:System.Windows.Forms.TextBox>\-Steuerelement namens `TextBox1` besitzen, müssen Sie für den Zugriff auf dessen <xref:System.Windows.Forms.TextBoxBase.Text%2A>\-Eigenschaft `TextBox1.Text` eingeben. Wenn Sie stattdessen `TextBox1Text` eingeben, haben Sie einen anderen Namen erstellt.  
  
## Siehe auch  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Visual Basic Naming Conventions](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [References to Declared Elements](/dotnet/visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements)