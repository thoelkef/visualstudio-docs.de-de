---
title: "Der Stammnamespace &lt;Namespacename&gt; ist nicht CLS-kompatibel. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40038"
  - "vbc40038"
helpviewer_keywords: 
  - "BC40038"
ms.assetid: ec850295-b2fe-4f19-b808-d22fe0aaa32d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Stammnamespace &lt;Namespacename&gt; ist nicht CLS-kompatibel.
Eine Assembly ist als `<CLSCompliant(True)>` gekennzeichnet, aber der Stammnamespacename beginnt mit einem Unterstrich \(`_`\).  
  
 Ein Programmierelement kann ein oder mehrere Unterstriche enthalten, aber damit es mit der [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) kompatibel ist, darf es nicht mit einem Unterstrich beginnen. Siehe [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> auf ein Programmierelement anwenden, legen Sie den `isCompliant`\-Parameter des Attributs auf `True` oder `False` fest, um die Kompatibilität bzw. Nichtkompatibilität anzugeben. Es gibt keinen Standardwert für diesen Parameter, und Sie müssen einen Wert angeben.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> nicht auf ein Element anwenden, wird dieses als nicht kompatibel betrachtet.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40038  
  
### So beheben Sie diesen Fehler  
  
-   Wenn die CLS\-Kompatibilität erforderlich ist, ändern Sie den Stammnamespacenamen, damit dieser nicht mit einem Unterstrich beginnt.  
  
-   Wenn der Stammnamespacename unverändert bleiben muss, entfernen Sie das <xref:System.CLSCompliantAttribute> aus der Assembly, oder markieren Sie sie als `<CLSCompliant(False)>`.  
  
## Siehe auch  
 [Namespace Statement](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Namespaces in Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces)   
 [\/rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace)   
 [NIB: Gewusst wie: Ändern des Namespaces für eine Anwendung \(Visual Basic\)](http://msdn.microsoft.com/de-de/029d85c0-e173-4f7a-afba-a29f3aaf6ebf)   
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Visual Basic Naming Conventions](/dotnet/visual-basic/programming-guide/program-structure/naming-conventions)   
 [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3)