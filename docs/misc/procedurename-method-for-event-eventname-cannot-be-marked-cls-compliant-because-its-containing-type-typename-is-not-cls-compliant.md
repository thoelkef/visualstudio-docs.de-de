---
title: "Die &#39;&lt;Prozedurname&gt;&#39;-Methode f&#252;r das Ereignis &#39;&lt;Ereignisname&gt;&#39; kann nicht als CLS-kompatibel gekennzeichnet werden, da sie den Typ &#39;&lt;Typname&gt;&#39; enthalten, der nicht CLS-kompatibel ist. | Microsoft Docs"
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
  - "vbc40053"
  - "bc40053"
helpviewer_keywords: 
  - "BC40053"
ms.assetid: 5f7aaf64-b5e6-4f97-9ebd-44cd4c7e8bf5
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &#39;&lt;Prozedurname&gt;&#39;-Methode f&#252;r das Ereignis &#39;&lt;Ereignisname&gt;&#39; kann nicht als CLS-kompatibel gekennzeichnet werden, da sie den Typ &#39;&lt;Typname&gt;&#39; enthalten, der nicht CLS-kompatibel ist.
Ein benutzerdefiniertes Ereignis deklariert eine `AddHandler`\- oder `RemoveHandler`\-Prozedur und kennzeichnet sie als `<CLSCompliant(True)>`, aber das Ereignis wird in einem Typ definiert, der als `<CLSCompliant(False)>` oder überhaupt nicht gekennzeichnet ist.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> auf ein Programmierelement anwenden, legen Sie den `isCompliant`\-Parameter des Attributs auf `True` oder `False` fest, um die Kompatibilität bzw. Nichtkompatibilität anzugeben. Es gibt keinen Standardwert für diesen Parameter, und Sie müssen einen Wert angeben.  
  
 Wenn Sie <xref:System.CLSCompliantAttribute> nicht auf ein Element anwenden, wird dieses als nicht kompatibel betrachtet.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40053  
  
### So beheben Sie diesen Fehler  
  
-   Wenn die CLS\-Kompatibilität erforderlich ist, definieren Sie das Ereignis innerhalb eines Typs, das CLS\-kompatibel ist.  
  
-   Wenn dieses Ereignis in seinem enthaltenden Typ verbleiben muss, entfernen Sie das <xref:System.CLSCompliantAttribute> aus seiner Definition, oder kennzeichnen Sie ihn als `<CLSCompliant(False)>`.  
  
## Siehe auch  
 [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)   
 [NICHT IM BUILD: AddHandler und RemoveHandler](http://msdn.microsoft.com/de-de/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)   
 [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3)