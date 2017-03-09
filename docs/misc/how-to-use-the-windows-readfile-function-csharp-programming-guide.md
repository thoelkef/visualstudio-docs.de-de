---
title: "Gewusst wie: Verwenden der ReadFile-Funktion von Windows (C#-Programmierhandbuch) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ReadFile-Funktion [C#]"
ms.assetid: 46bb53e0-a658-48c9-ae36-6720da7781c1
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "billchi"
manager: "douge"
---
# Gewusst wie: Verwenden der ReadFile-Funktion von Windows (C#-Programmierhandbuch)
In diesem Beispiel wird durch das Lesen und Anzeigen einer Textdatei die `ReadFile`\-Funktion von Windows veranschaulicht.  Für die `ReadFile`\-Funktion muss `unsafe`\-Code verwendet werden, da ein Zeiger als Parameter benötigt wird.  
  
 Das an die `Read`\-Funktion übergebene Bytearray ist ein verwalteter Typ.  Dies bedeutet, dass der Garbage Collector der Common Language Runtime \(CLR\) den vom Array belegten Speicher beliebig verschieben kann.  Um dies zu verhindern, wird mithilfe von [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) ein Zeiger auf den Speicher abgerufen und gekennzeichnet, damit der Garbage Collector diesen nicht verschieben kann.  Am Ende des `fixed`\-Blocks wird der Speicher automatisch wieder in den Zustand zurückgesetzt, in dem er Verschiebungen durch die Garbage Collection unterliegt.  
  
 Diese Möglichkeit wird als *deklaratives Fixieren* bezeichnet.  Beim Fixieren ist der Verwaltungsaufwand sehr gering, sofern die Garbage Collection nicht im `fixed`\-Block auftritt. Dies ist jedoch nur sehr selten der Fall.  Fixieren kann jedoch zu einigen unerwünschten Seiteneffekten beim Ausführen der globalen Garbage Collection führen.  Die Garbage Collector\-Fähigkeit zum Komprimieren von Speicher wird durch fixierte Puffer stark beeinträchtigt.  Aus diesem Grund sollte das Fixieren nach Möglichkeit vermieden werden.  
  
## Beispiel  
 [!code-cs[csProgGuidePointers#2](../misc/codesnippet/CSharp/how-to-use-the-windows-readfile-function-csharp-programming-guide_1.cs)]  
  
## Siehe auch  
 [C\#\-Programmierhandbuch](/dotnet/csharp/programming-guide/index)   
 [C\#\-Referenz](/dotnet/csharp/language-reference/index)   
 [Unsicherer Code und Zeiger](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)   
 [Zeigertypen](/dotnet/csharp/programming-guide/unsafe-code-pointers/pointer-types)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)