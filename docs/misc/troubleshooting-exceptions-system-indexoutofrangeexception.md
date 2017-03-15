---
title: "Problembehandlung bei Ausnahmen: System.IndexOutOfRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "IndexOutOfRangeException-Klasse"
ms.assetid: 9e28623c-93fc-4111-a0cb-c380e0b5de0c
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IndexOutOfRangeException
Eine <xref:System.IndexOutOfRangeException>\-Ausnahme wird bei dem Versuch ausgelöst, auf ein Array\- oder Auflistungselement zuzugreifen, dessen Index kleiner als 0 \(null\) ist oder außerhalb der vom Array vorgegebenen Grenzen liegt.  
  
## Tipps  
 **Stellen Sie sicher, dass der maximale Index einer Liste kleiner als die Listengröße ist.**  
 Der maximale Index einer Liste muss kleiner sein als die Anzahl der Listenelemente.  
  
 **Stellen Sie sicher, dass der Index keine negative Zahl ist.**  
 Diese Ausnahme wird ausgelöst, wenn der Index kleiner als 0 \(null\) ist.  
  
 **Stellen Sie sicher, dass die Spaltennamen richtig sind.**  
 Diese Ausnahme wird möglicherweise ausgelöst, wenn ein ungültiger Datenspaltenname an die <xref:System.Data.DataView.Sort%2A?displayProperty=fullName>\-Eigenschaft übergeben wird. Weitere Informationen finden Sie in den Ausführungen zur <xref:System.Data.DataView>\-Klasse.  
  
## Beispiel  
  
### Beschreibung  
 Das folgende Beispiel fängt die `Try…Catch` mithilfe eines `IndexOutOfRangeException`\-Blocks ab, wenn Index `i` außerhalb der Arraygrenzen 0 bis 3 liegt. Im folgenden Beispiel wird Folgendes angezeigt.  
  
 `Element at index 0: 3`  
  
 `Element at index 2: 5`  
  
 `Element at index -1: IndexOutOfRangeException caught`  
  
 `Element at index 4: IndexOutOfRangeException caught`  
  
### Code  
  
```vb#  
Module Module1 Sub Main() ' The first two tests will display the value of the array element. IndexTest(0) IndexTest(2) ' The following two calls will display the information that ' an IndexOutOfRangeException was caught. IndexTest(-1) IndexTest(4) End Sub Sub IndexTest(ByVal i As Integer) Dim testArray() As Integer = {3, 4, 5, 6} Console.Write("Element at index {0}: ", i) Try Console.WriteLine(testArray(i)) Catch ex As IndexOutOfRangeException Console.WriteLine("IndexOutOfRangeException caught") End Try End Sub End Module  
```  
  
## Siehe auch  
 <xref:System.IndexOutOfRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)