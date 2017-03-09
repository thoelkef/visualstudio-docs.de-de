---
title: "Vor dem Zeilenfortsetzungszeichen &quot;_&quot; muss mindestens eine Leerstelle stehen, und es muss das letzte Zeichen der Zeile sein. | Microsoft Docs"
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
  - "vbc30999"
  - "bc30999"
helpviewer_keywords: 
  - "BC30999"
ms.assetid: 32caf62f-52e4-4acd-b40f-5af65e42e643
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vor dem Zeilenfortsetzungszeichen &quot;_&quot; muss mindestens eine Leerstelle stehen, und es muss das letzte Zeichen der Zeile sein.
Sie können das Zeilenfortsetzungszeichen \(das durch einen Unterstrich \(\_\) dargestellt wird\) auch verwenden, um eine lange Codezeile auf mehrere Zeilen in der Datei zu verteilen. Dem Unterstrich muss ein Leerzeichen direkt vorangestellt und ein Zeilenabschlusszeichen \(Wagenrücklauf\) direkt nachgestellt sein. Zum Beispiel:  
  
```  
Dim books As XDocument = _ XDocument.Load(My.Application.Info.DirectoryPath & _ "\..\..\Data\books.xml")  
```  
  
 **Fehler\-ID:** BC30999  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass das Zeilenfortsetzungszeichen \(\_\) das letzte Zeichen in einer Codezeile ist.  
  
2.  Stellen Sie sicher, dass dem Zeilenfortsetzungszeichen ein Leerzeichen vorangestellt ist, durch das es von anderem Code in der Zeile getrennt wird.  
  
## Siehe auch  
 [Gewusst wie: Umbrechen und Zusammenfassen von Anweisungen in Code](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)