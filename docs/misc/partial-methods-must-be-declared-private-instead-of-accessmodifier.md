---
title: "Partielle Methoden m&#252;ssen als &#39;Private&#39; deklariert werden, nicht als &#39;&lt;Zugriffsmodifizierer&gt;&#39;. | Microsoft Docs"
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
  - "vbc31431"
  - "bc31431"
helpviewer_keywords: 
  - "BC31431"
ms.assetid: bbd757f3-7281-4488-8a06-f3b4bcc820dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Partielle Methoden m&#252;ssen als &#39;Private&#39; deklariert werden, nicht als &#39;&lt;Zugriffsmodifizierer&gt;&#39;.
Der Zugriffsmodifizierer `Private` ist in Deklarationen partieller Methoden erforderlich. Das folgende Beispiel zeigt die Verwendung von `Private` in der Methodensignatur und die entsprechende Implementierung.  
  
```vb#  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```vb#  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **Fehler\-ID:** BC31431  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Zugriffsmodifizierer in den Signatur\- und Implementierungsdeklarationen in `Private`.  
  
## Siehe auch  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)