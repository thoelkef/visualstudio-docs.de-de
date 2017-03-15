---
title: "Die Structure-Einschr&#228;nkung und eine Einschr&#228;nkung f&#252;r einen spezifischen Klassentyp k&#246;nnen nicht kombiniert werden | Microsoft Docs"
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
  - "vbc32108"
  - "bc32108"
helpviewer_keywords: 
  - "BC32108"
ms.assetid: de461824-5aec-48d1-967d-b0e0609a8ba6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Structure-Einschr&#228;nkung und eine Einschr&#228;nkung f&#252;r einen spezifischen Klassentyp k&#246;nnen nicht kombiniert werden
Eine Einschränkungsliste enthält sowohl die Einschränkung [Stucture \(Visual Basic\)](http://msdn.microsoft.com/de-de/263ce115-ac36-4c05-8cb7-0e0eead5c6d0) als auch den Namen einer definierten Klasse.  
  
 Eine Einschränkungsliste erzwingt Anforderungen an das Typargument, das an den Typparameter übergeben wird. Sie können die folgenden Anforderungen in beliebiger Kombination angeben:  
  
-   Das Typargument muss mindestens eine Schnittstelle implementieren.  
  
-   Das Typargument darf von höchstens einer Klasse erben.  
  
-   Das Typargument muss einen parameterlosen Konstruktor verfügbar machen, auf den der erstellende Code zugreifen kann \(die `New`\-Einschränkung muss enthalten sein\)  
  
 Wenn Sie keine bestimmte Klasse oder Schnittstelle in die Einschränkungsliste aufnehmen, können Sie eine allgemeinere Anforderung festlegen, indem Sie eine der folgenden Festlegungen treffen:  
  
-   Das Typargument muss ein Werttyp sein \(die Einschränkung `Structure` enthalten\)  
  
-   Das Typargument muss ein Verweistyp sein \(die Einschränkung `Class` enthalten\)  
  
 Sie können nicht sowohl `Structure` als auch `Class` für den gleichen Typparameter angeben, und Sie können jedes Schlüsselwort nur einmal angeben.  
  
 **Fehler\-ID:** BC32108  
  
### So beheben Sie diesen Fehler  
  
-   Soll das Typargument ein Werttyp sein, entfernen Sie den Klassennamen aus der Einschränkungsliste.  
  
-   Wenn das Typargument vom angegebenen Klassennamen erben soll, entfernen Sie das Schlüsselwort `Structure` aus der Einschränkungsliste.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)