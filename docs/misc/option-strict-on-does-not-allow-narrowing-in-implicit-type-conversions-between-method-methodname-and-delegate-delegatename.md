---
title: "„Option Strict On“ l&#228;sst keine Einschr&#228;nkungen in impliziten Typkonvertierungen zwischen der Methode &#39;&lt;Methodenname&gt;&#39; und dem Delegaten &#39;&lt;Delegatname&gt;&#39; zu. | Microsoft Docs"
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
  - "bc36663"
  - "vbc36663"
helpviewer_keywords: 
  - "BC36663"
ms.assetid: fefc7ab5-b587-4ff9-a6bc-4c4e5d4b6b29
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# „Option Strict On“ l&#228;sst keine Einschr&#228;nkungen in impliziten Typkonvertierungen zwischen der Methode &#39;&lt;Methodenname&gt;&#39; und dem Delegaten &#39;&lt;Delegatname&gt;&#39; zu.
Mit „`Option Strict` On“ können Sie keine einschränkende Konvertierung zwischen dem Datentyp eines Parameters in einem Delegaten und dem entsprechenden Parameter einer Funktion oder `Sub`, der einer Variablen dieses Delegattyps zugewiesen ist, vornehmen. Der Funktionsdelegat `Del` verfügt z. B. über einen Parameter vom Typ `Integer`, während die Funktionen `Conversion1`, `Conversion2`, und `Conversion3` über einen Parameter mit unterschiedlichen numerischen Typen verfügen.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String Function Conversion1(ByVal n As Integer) As String Return "Valid" End Function Function Conversion2(ByVal n As Long) As String Return "Valid" End Function Function Conversion3(ByVal n As Short) As String Return "Not valid" End Function  
```  
  
 Da eine erweiternde Konvertierung von `Integer` in `Integer` und in `Long` erfolgt, sind die folgenden Zuweisungen gültig.  
  
```vb#  
' Valid. Dim funDel1 As Del = AddressOf Conversion1 Dim funDel2 As Del = AddressOf Conversion2  
```  
  
 Die Konvertierung von `Integer` in `Short` ist eine einschränkende Konvertierung. Daher ist die folgende Zuordnung ungültig.  
  
```vb#  
' Not valid. Dim funDel3 As Del = AddressOf Conversion3  
```  
  
 Fehler\-ID: BC36663  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Datentyp des Parameters im Delegaten oder der Methode so, dass sich die erforderliche erweiternde Beziehung ergibt.  
  
## Siehe auch  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegates](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [NICHT IM BUILD: Delegaten und der AddressOf\-Operator](http://msdn.microsoft.com/de-de/7b2ed932-8598-4355-b2f7-5cedb23ee86f)