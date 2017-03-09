---
title: "Ein nicht CLS-kompatibler MustOverride-Member ist in &lt;Klassenname&gt; (CLS-kompatibel) nicht zul&#228;ssig. | Microsoft Docs"
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
  - "bc40034"
  - "vbc40034"
helpviewer_keywords: 
  - "BC40034"
ms.assetid: 4eb36b3a-1bbe-4e99-9ecb-a12b8729b128
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein nicht CLS-kompatibler MustOverride-Member ist in &lt;Klassenname&gt; (CLS-kompatibel) nicht zul&#228;ssig.
Eine Klasse ist als `<CLSCompliant(True)>` markiert, enthält aber eine `MustOverride`\-Eigenschaft oder \-Prozedur, die als `<CLSCompliant(False)>` oder gar nicht markiert ist.  
  
 Wenn eine Klasse mit der [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) kompatibel ist, greift eine Anwendung, die diese Klasse verwendet, nur auf die Member zu, die auch als `<CLSCompliant(True)>` markiert sind und ignoriert andere Member. Die Anwendung kann eine `MustOverride`\-Eigenschaft oder \-Prozedur jedoch nicht ignorieren, weil sie auf diese Eigenschaft bzw. Prozedur zugreifen muss, um sie außer Kraft zu setzen.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> auf ein Programmierelement anwenden, legen Sie den `isCompliant`\-Parameter des Attributs auf `True` oder `False` fest, um die Kompatibilität bzw. Nichtkompatibilität anzugeben. Es gibt keinen Standardwert für diesen Parameter, und Sie müssen einen Wert angeben.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> nicht auf ein Element anwenden, wird dieses als nicht kompatibel betrachtet.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40034  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie CLS\-Kompatibilität benötigen und die Kontrolle über den Quellcode für die Klasse haben, markieren Sie den Member als `<CLSCompliant(True)>`.  
  
-   Wenn Sie CLS\-Kompatibilität benötigen und keine Kontrolle über den Quellcode für die Klasse haben, oder wenn der Quellcode nicht kompatibel ist, definieren Sie den Member in einer anderen Klasse.  
  
-   Wenn dieser Member nicht kompatibel sein darf, entfernen Sie das `MustOverride`\-Schlüsselwort aus seiner Definition, entfernen Sie <xref:System.CLSCompliantAttribute> aus der Klassendefinition, oder markieren Sie die Klasse als `<CLSCompliant(False)>`.  
  
## Siehe auch  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3)