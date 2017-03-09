---
title: "&#39;&lt;Elementname&gt;&#39; f&#252;r den Imports-Alias f&#252;r &#39;&lt;Qualifizierter_Elementname&gt;&#39; bezieht sich nicht auf einen Namespace, eine Klasse, eine Struktur, eine Schnittstelle, eine Enumeration oder ein Modul. | Microsoft Docs"
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
  - "bc30798"
  - "vbc30798"
helpviewer_keywords: 
  - "BC30798"
ms.assetid: bfa66627-516a-4955-977d-92372bcea090
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Elementname&gt;&#39; f&#252;r den Imports-Alias f&#252;r &#39;&lt;Qualifizierter_Elementname&gt;&#39; bezieht sich nicht auf einen Namespace, eine Klasse, eine Struktur, eine Schnittstelle, eine Enumeration oder ein Modul.
Ein [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) gibt ein Programmierelement an, das nicht importiert werden kann.  
  
 Die `Imports`\-Anweisung wird zum Verringern oder Entfernen der Anforderung nach einer qualifizierenden Zeichenfolge vor einem Elementnamen verwendet. Sie qualifizieren das Element in der `Imports`\-Anweisung selbst, um einen eindeutigen Pfad zu einer eindeutigen Deklaration des Elements anzugeben. Danach müssen Sie keine Verweise auf das Element zu qualifizieren.  
  
 `Imports` wird am häufigsten für Namespaces verwendet, aber Sie können auch eine Klasse, ein Modul, eine Struktur, eine Schnittstelle oder eine Enumeration verwenden, um Verweise ohne lange qualifizierende Zeichenfolge auf ihre Elemente zu erlauben.  
  
 Weitere Informationen finden Sie unter „Importieren von enthaltenen Elementen“ in [NOTINBUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9).  
  
 **Fehler\-ID:** BC30798  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise der Elemente in der Qualifizierungszeichenfolge in der `Imports`\-Anweisung, insbesondere das letzte Element in der Zeichenfolge, bei dem es sich um das qualifizierende Element handelt.  
  
2.  Überprüfen Sie, ob das qualifizierende Element einen geeigneten Typ \(Namespace, Klasse, Modul, Struktur, Schnittstelle oder Enumeration\) aufweist. Entfernen Sie andernfalls die `Imports`\-Anweisung.  
  
## Siehe auch  
 [References and the Imports Statement](/dotnet/visual-basic/programming-guide/program-structure/references-and-the-imports-statement)