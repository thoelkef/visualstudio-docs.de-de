---
title: "Partielle Methoden m&#252;ssen als &quot;Private&quot; deklariert werden | Microsoft Docs"
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
  - "vbc31432"
  - "bc31432"
helpviewer_keywords: 
  - "BC31432"
ms.assetid: 3a4474d9-661e-4793-9624-30cf81faddcf
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Partielle Methoden m&#252;ssen als &quot;Private&quot; deklariert werden
Der Zugriffsmodifizierer `Private` ist in Deklarationen partieller Methoden erforderlich. Das folgende Beispiel zeigt die Verwendung von `Private` in der Methodensignatur und die entsprechende Implementierung.  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **Fehler\-ID:** BC31432  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie das Schlüsselwort `Private` vor `Sub` in den Deklarationen der Signatur und Implementierung hinzu.  
  
## Siehe auch  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)