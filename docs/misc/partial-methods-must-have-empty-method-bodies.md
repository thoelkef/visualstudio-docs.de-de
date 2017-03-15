---
title: "Der Text von partiellen Methoden muss leer sein. | Microsoft Docs"
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
  - "bc31435"
  - "vbc31435"
helpviewer_keywords: 
  - "BC31435"
ms.assetid: 279f283d-ce40-401c-8494-4bf06394fdd3
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Text von partiellen Methoden muss leer sein.
Der Text der Deklaration einer partiellen Methodensignatur darf keinen Code enthalten. Das folgende Beispiel zeigt die Signatur einer partiellen Methode und ihre Implementierung.  
  
```  
' Definition of the partial method signature. Partial Private Sub OnNameChanged() ' The body of the signature is empty. End Sub  
```  
  
```  
' Implementation of the partial method. Private Sub OnNameChanged() MsgBox("Name was changed to " & Me.Name) End Sub  
```  
  
 **Fehler\-ID:** 31435  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie sämtlichen Code aus der Deklaration der partiellen Methode.  
  
## Siehe auch  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)