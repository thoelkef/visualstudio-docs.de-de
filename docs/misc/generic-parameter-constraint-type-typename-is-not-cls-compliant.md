---
title: "Der Einschr&#228;nkungstyp &quot;&lt;Typname&gt;&quot; f&#252;r generische Parameter ist nicht CLS-kompatibel | Microsoft Docs"
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
  - "bc40040"
  - "vbc40040"
helpviewer_keywords: 
  - "BC40040"
ms.assetid: c640dd59-56a9-43ed-b199-32a60f7b9b06
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Einschr&#228;nkungstyp &quot;&lt;Typname&gt;&quot; f&#252;r generische Parameter ist nicht CLS-kompatibel
Ein generischer Typ ist als `<CLSCompliant(True)>` markiert, aber eine Einschränkung für einen seiner Typparameter gibt einen Typ an, der als `<CLSCompliant(False)>` markiert ist, nicht markiert ist oder nicht geeignet ist, weil es sich um einen nicht kompatiblen Typ handelt.  
  
 Wenn ein Typ mit der [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) kompatibel sein soll, darf er nur CLS\-kompatible Typen verwenden. Dies gilt auch für die Einschränkungen von Typparametern eines generischen Typs.  
  
 Die folgenden [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Datentypen sind nicht CLS\-kompatibel:  
  
-   [SByte Data Type](/dotnet/visual-basic/language-reference/data-types/sbyte-data-type)  
  
-   [UInteger Data Type](/dotnet/visual-basic/language-reference/data-types/uinteger-data-type)  
  
-   [ULong Data Type](/dotnet/visual-basic/language-reference/data-types/ulong-data-type)  
  
-   [UShort Data Type](/dotnet/visual-basic/language-reference/data-types/ushort-data-type)  
  
 Wenn Sie das <xref:System.CLSCompliantAttribute>\-Attribut auf ein Programmierelement anwenden, legen Sie den `isCompliant`\-Parameter des Attributs auf `True` oder `False` fest, um die Kompatibilität bzw. Nichtkompatibilität anzugeben. Es gibt keinen Standardwert für diesen Parameter, und Sie müssen einen Wert angeben.  
  
 Wenn Sie <xref:System.CLSCompliantAttribute> nicht auf ein Element anwenden, wird dieses als nicht kompatibel betrachtet.  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40040  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie <xref:System.CLSCompliantAttribute>, wenn der generische Typ einen auf diesen speziellen Typ eingeschränkten Typparameter akzeptieren muss. Der Typ kann nicht CLS\-kompatibel sein.  
  
-   Wenn der generische Typ CLS\-kompatibel sein muss, ändern Sie den Typ dieser Einschränkung in den ähnlichsten CLS\-kompatiblen Typ. Anstelle von `UInteger` könnten Sie beispielsweise `Integer` verwenden, wenn Sie den Wertebereich über 2.147.483.647 nicht benötigen. Wenn Sie den erweiterten Bereich benötigen, können Sie `UInteger` durch `Long` ersetzen.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [\<PAVE OVER\> Schreiben von CLS\-kompatiblem Code](http://msdn.microsoft.com/de-de/4c705105-69a2-4e5e-b24e-0633bc32c7f3)