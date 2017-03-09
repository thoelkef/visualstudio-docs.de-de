---
title: "Die Signatur der &lt;Methodenname&gt;-Methode ist mit dem Delegaten &quot;&lt;Delegatenname&gt;&quot; nicht kompatibel. | Microsoft Docs"
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
  - "vbc31143"
  - "bc31143"
helpviewer_keywords: 
  - "BC31143"
ms.assetid: 88990637-7c92-467e-a3d3-db5498dc1dce
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Signatur der &lt;Methodenname&gt;-Methode ist mit dem Delegaten &quot;&lt;Delegatenname&gt;&quot; nicht kompatibel.
Dieser Fehler tritt auf, wenn eine Konvertierung zwischen einer Methode und einem Delegaten erforderlich ist, die nicht möglich ist. Die Ursache des Fehlers kann eine Konvertierung zwischen Parametern oder, wenn die Methode und der Delegat Funktionen sind, eine Konvertierung in den Rückgabewerten sein.  
  
 Das folgende Codebeispiel veranschaulicht fehlgeschlagene Konvertierungen.`FunDel` ist der Delegat.  
  
```vb#  
Delegate Function FunDel(ByVal i As Integer, ByVal d As Double) As Integer  
```  
  
 Jede der folgenden Funktionen unterscheidet sich von `FunDel` in einer Weise, die diesen Fehler verursacht.  
  
```vb#  
Function ExampleMethod1(ByVal m As Integer, ByVal aDate As Date) As Integer End Function Function ExampleMethod2(ByVal m As Integer, ByVal aDouble As Double) As Date End Function  
```  
  
 Jede der folgenden Zuweisungsanweisungen verursacht den Fehler.  
  
```vb#  
Sub Main() ' The second parameters of FunDel and ExampleMethod1, Double and Date, ' are not compatible. 'Dim d1 As FunDel = AddressOf ExampleMethod1 ' The return types of FunDel and ExampleMethod2, Integer and Date, ' are not compatible. 'Dim d2 As FunDel = AddressOf ExampleMethod2 End Sub  
```  
  
 **Fehler\-ID:** BC31143  
  
### So beheben Sie diesen Fehler  
  
-   Untersuchen Sie die entsprechenden Parameter und, sofern vorhanden, Rückgabetypen, um zu ermitteln, welches Paar nicht kompatibel ist.  
  
## Siehe auch  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [NICHT IM BUILD: Delegaten und der AddressOf\-Operator](http://msdn.microsoft.com/de-de/7b2ed932-8598-4355-b2f7-5cedb23ee86f)