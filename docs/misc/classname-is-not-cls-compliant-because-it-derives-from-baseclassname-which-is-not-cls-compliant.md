---
title: "&#39;&lt;klassenname&gt;&#39; ist nicht CLS-kompatibel, da sie aus &#39;&lt;basisklassenname&gt;&#39; abgeleitet ist, die nicht CLS-kompatibel ist | Microsoft Docs"
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
  - "vbc40026"
  - "bc40026"
helpviewer_keywords: 
  - "BC40026"
ms.assetid: debcd5e4-75e7-4b14-a6cc-18f1009fe52c
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;klassenname&gt;&#39; ist nicht CLS-kompatibel, da sie aus &#39;&lt;basisklassenname&gt;&#39; abgeleitet ist, die nicht CLS-kompatibel ist
Eine Klasse oder Schnittstelle wird als `<CLSCompliant(True)>` gekennzeichnet, wenn sie von einem Typ abgeleitet ist oder einen Typ implementiert, der als `<CLSCompliant(False)>` oder gar nicht gekennzeichnet ist.  
  
 Damit eine Klasse oder Schnittstelle mit der [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) kompatibel ist, muss ihre gesamte Vererbungshierarchie kompatibel sein. Das bedeutet, dass jeder Typ, von dem sie direkt oder indirekt erbt, kompatibel sein muss. Analog dazu muss eine Klasse, wenn sie eine oder mehrere Schnittstellen implementiert, deren Kompatibilität durch alle Vererbungshierarchien sicherstellen.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> auf ein Programmierelement anwenden, legen Sie den `isCompliant`\-Parameter des Attributs auf `True` oder `False` fest, um die Kompatibilität bzw. Nichtkompatibilität anzugeben. Es gibt keinen Standardwert für diesen Parameter, und Sie müssen einen Wert angeben.  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute> nicht auf ein Element anwenden, wird dieses als nicht kompatibel betrachtet.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40026  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie CLS\-Kompatibilität benötigen, definieren Sie diesen Typ innerhalb einer anderen Vererbungshierarchie oder eines anderen Implementierungsschemas.  
  
-   Wenn dieser Typ in der aktuellen Vererbungshierarchie oder dem aktuellen Implementierungsschema verbleiben muss, entfernen Sie das <xref:System.CLSCompliantAttribute> aus seiner Definition, oder kennzeichnen Sie ihn als `<CLSCompliant(False)>`.  
  
## Siehe auch  
 [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3)