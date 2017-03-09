---
title: "&#39;AddressOf&#39; kann nicht auf &#39;methodenname&#39; angewendet werden, da &#39;methodenname&#39; eine partielle Methode ist | Microsoft Docs"
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
  - "vbc31440"
  - "bc31440"
helpviewer_keywords: 
  - "BC31440"
ms.assetid: 924dbada-3e0a-4004-a3ae-a209b7c3d1fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;AddressOf&#39; kann nicht auf &#39;methodenname&#39; angewendet werden, da &#39;methodenname&#39; eine partielle Methode ist
Eine partielle Methode wurde dem `AddressOf`\-Operator übergeben. Partielle Methoden stellen ungültige Werte für den `AddressOf`\-Operator dar.  
  
 **Fehler\-ID:** BC31440  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie eine Implementierungsmethode für die partielle Methode hinzu. Die Implementierungsmethode ist ein gültiger Wert für den `AddressOf`\-Operator. Das folgende Beispiel zeigt die Signatur einer partiellen Methode und ihre Implementierung.  
  
    ```vb#  
    ' Definition of the partial method signature.  
    Partial Private Sub OnNameChanged()  
        ' The body of the signature is empty.  
    End Sub  
  
    ' Implementation of the partial method.  
    Private Sub OnNameChanged()  
        MsgBox("Name was changed to " & Me.Name)  
    End Sub  
    ```  
  
## Siehe auch  
 [AddressOf Operator](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)