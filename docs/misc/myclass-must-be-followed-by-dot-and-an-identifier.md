---
title: "Auf „MyClass“ m&#252;ssen ein Punkt (.) und ein Bezeichner folgen. | Microsoft Docs"
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
  - "bc32028"
  - "vbc32028"
helpviewer_keywords: 
  - "BC32028"
ms.assetid: a7e92b54-32b8-4072-9576-632942f05e0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auf „MyClass“ m&#252;ssen ein Punkt (.) und ein Bezeichner folgen.
`MyClass` ist keine echte Objektvariable und darf nicht allein stehen. Sie verwenden „MyClass“ nur, um auf einen Member der aktuellen Instanz zuzugreifen, als wäre er `NotOverridable` in der Basisklasse.  
  
 **Fehler\-ID:** BC32028  
  
### So beheben Sie diesen Fehler  
  
1.  Wenn Sie auf einen Klassenmember zugreifen möchten, geben Sie den Memberzugriffsoperator \(`.`\) und einen Member der aktuellen Instanz nach `MyClass` ein.  
  
2.  Wenn Sie nicht auf einen Klassenmember zugreifen möchten, verwenden Sie das `Me`\-Schlüsselwort.  
  
## Siehe auch  
 [MyClass – löschen](http://msdn.microsoft.com/de-de/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [Me](http://msdn.microsoft.com/de-de/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)