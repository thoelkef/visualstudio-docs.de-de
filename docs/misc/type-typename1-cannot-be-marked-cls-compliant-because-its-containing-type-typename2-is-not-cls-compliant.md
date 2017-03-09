---
title: "Der Typ &#39;&lt;Typame1&gt;&#39; kann nicht als CLS-kompatibel gekennzeichnet werden, da er den Typ &#39;&lt;Typname1&gt;&#39; enth&#228;lt, der nicht CLS-kompatibel ist. | Microsoft Docs"
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
  - "vbc40030"
  - "bc40030"
helpviewer_keywords: 
  - "BC40030"
ms.assetid: f1cfcf04-2a99-46ef-ac87-34cc2099125c
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typ &#39;&lt;Typame1&gt;&#39; kann nicht als CLS-kompatibel gekennzeichnet werden, da er den Typ &#39;&lt;Typname1&gt;&#39; enth&#228;lt, der nicht CLS-kompatibel ist.
Eine Klasse oder Schnittstelle wird als `<CLSCompliant(True)>` gekennzeichnet, wenn sie in einem Typ geschachtelt ist, der als `<CLSCompliant(False)>` oder gar nicht gekennzeichnet ist.  
  
 Damit eine Klasse oder Schnittstelle mit der [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) kompatibel ist, muss die gesamte Kapselungshierarchie kompatibel sein. Das bedeutet, dass jeder Typ, in dem sie geschachtelt ist, kompatibel sein muss.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> auf ein Programmierelement anwenden, legen Sie den `isCompliant`\-Parameter des Attributs auf `True` oder `False` fest, um die Kompatibilität bzw. Nichtkompatibilität anzugeben. Es gibt keinen Standardwert für diesen Parameter, und Sie müssen einen Wert angeben.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> nicht auf ein Element anwenden, wird dieses als nicht kompatibel betrachtet.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40030  
  
### So beheben Sie diesen Fehler  
  
-   Wenn die CLS\-Kompatibilität erforderlich ist, definieren Sie diesen Typ in einer anderen Kapselungshierarchie.  
  
-   Wenn dieser Typ in der aktuellen Kapselungshierarchie verbleiben muss, entfernen Sie das <xref:System.CLSCompliantAttribute> aus seiner Definition, oder kennzeichnen Sie ihn als `<CLSCompliant(False)>`.  
  
## Siehe auch  
 [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3)