---
title: "„System.CLSCompliantAttribute“ kann nicht auf die Get-/Set-Eigenschaft angewendet werden. | Microsoft Docs"
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
  - "vbc40043"
  - "BC40043"
helpviewer_keywords: 
  - "BC40043"
ms.assetid: 2ff45c09-32be-4ca9-b42a-63ce2536db7d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „System.CLSCompliantAttribute“ kann nicht auf die Get-/Set-Eigenschaft angewendet werden.
Eine Eigenschaftendefinition wendet das <xref:System.CLSCompliantAttribute>\-Attribut auf seine `Get`\- oder `Set`\-Anweisung an.  
  
 Damit eine Eigenschaft mit der [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) kompatibel ist, muss die gesamte Eigenschaft als `<CLSCompliant(True)>` gekennzeichnet werden. Sie müssen <xref:System.CLSCompliantAttribute> auf die [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) anwenden, nicht auf die `Get`\- oder die `Set`\-Anweisung.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> auf ein Programmierelement anwenden, legen Sie den `isCompliant`\-Parameter des Attributs auf `True` oder `False` fest, um die Kompatibilität bzw. Nichtkompatibilität anzugeben. Es gibt keinen Standardwert für diesen Parameter, und Sie müssen einen Wert angeben.  
  
 Wenn Sie <xref:System.CLSCompliantAttribute> nicht auf ein Element anwenden, wird dieses als nicht kompatibel betrachtet.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40043  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das <xref:System.CLSCompliantAttribute> aus der `Get`\- oder `Set`\-Anweisung.  
  
-   Wenn die Eigenschaft CLS\-kompatibel sein soll, kennzeichnen Sie die `Property`\-Anweisung als `<CLSCompliant(True)>`.  
  
## Siehe auch  
 [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)