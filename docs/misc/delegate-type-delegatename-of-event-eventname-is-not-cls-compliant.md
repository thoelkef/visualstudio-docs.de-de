---
title: "Der Delegattyp &#39;&lt;delegatname&gt;&#39; des Ereignisses &#39;&lt;ereignisname&gt;&#39; ist nicht CLS-kompatibel | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40050"
  - "vbc40050"
helpviewer_keywords: 
  - "BC40050"
ms.assetid: 92f5be26-9a82-46d4-bf97-005f2c7ca424
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Delegattyp &#39;&lt;delegatname&gt;&#39; des Ereignisses &#39;&lt;ereignisname&gt;&#39; ist nicht CLS-kompatibel
Ein [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement) verwendet einen Delegaten zur Angabe seiner Signatur, das [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement) ist aber als `<CLSCompliant(False)>` markiert oder gar nicht markiert.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute>\-Attribut auf ein Programmierelement anwenden, legen Sie den `isCompliant`\-Parameter des Attributs auf `True` oder `False` fest, um die Kompatibilität bzw. Nichtkompatibilität anzugeben. Es gibt keinen Standardwert für diesen Parameter, und Sie müssen einen Wert angeben.  
  
 Wenn Sie <xref:System.CLSCompliantAttribute> nicht auf ein Element anwenden, wird dieses als nicht kompatibel betrachtet.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40050  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie CLS\-Kompatibilität benötigen und Kontrolle über die Definition des Delegaten haben, wenden Sie <xref:System.CLSCompliantAttribute> auf seine Deklaration an, um ihn als `<CLSCompliant(True)>` zu kennzeichnen.  
  
-   Wenn Sie keine Kontrolle über die Definition des Delegaten haben oder ihn nicht als kompatibel kennzeichnen können, entfernen Sie das <xref:System.CLSCompliantAttribute> aus der `Event`\-Anweisung, oder markieren Sie sie als `<CLSCompliant(False)>`.  
  
## Siehe auch  
 [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3)