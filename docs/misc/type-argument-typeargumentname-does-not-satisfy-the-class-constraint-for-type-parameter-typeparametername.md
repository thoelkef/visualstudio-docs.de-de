---
title: "Das Typargument &#39;&lt;typargumentname&gt;&#39; entspricht nicht der &#39;Class&#39;-Einschr&#228;nkung f&#252;r den &#39;&lt;typparametername&gt;&#39;-Typparameter | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32106"
  - "bc32106"
helpviewer_keywords: 
  - "BC32106"
ms.assetid: 1bac1dd6-f86b-4e98-ba2d-57d1936e3658
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Typargument &#39;&lt;typargumentname&gt;&#39; entspricht nicht der &#39;Class&#39;-Einschr&#228;nkung f&#252;r den &#39;&lt;typparametername&gt;&#39;-Typparameter
Ein für einen generischen Typ angegebenes Typargument entspricht nicht der Verweistypeinschränkung für den entsprechenden Typparameter.  
  
 Eine Einschränkungsliste erzwingt Anforderungen an das Typargument, das an den Typparameter übergeben wird. Wenn Sie der Einschränkungsliste keine bestimmte Klasse oder Schnittstelle hinzufügen, können Sie eine allgemeine Anforderung festlegen, indem Sie eine der folgenden Bedingungen angeben:  
  
-   Das Typargument muss ein Werttyp sein \(fügen Sie die Einschränkung [Structure \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) hinzu\).  
  
-   Das Typargument muss ein Verweistyp sein \(fügen Sie die Einschränkung [Class \(Visual Basic\)](http://msdn.microsoft.com/de-de/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) hinzu\).  
  
 Sie können nicht sowohl `Structure` als auch `Class` für den gleichen Typparameter angeben, und Sie können jedes Schlüsselwort nur einmal angeben.  
  
 **Fehler\-ID:** BC32106  
  
### So beheben Sie diesen Fehler  
  
-   Wählen Sie ein Typargument mit einem beliebigen Verweistyp aus.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Gewusst wie: Verwenden einer generischen Klasse](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)