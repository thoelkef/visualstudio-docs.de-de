---
title: "Initialisierer f&#252;r Strukturmember sind nur f&#252;r Shared-Member und -Konstanten g&#252;ltig. | Microsoft Docs"
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
  - "bc31049"
  - "vbc31049"
helpviewer_keywords: 
  - "BC31049"
ms.assetid: 8356978e-7f84-4932-be0f-dda005c9f8ca
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Initialisierer f&#252;r Strukturmember sind nur f&#252;r Shared-Member und -Konstanten g&#252;ltig.
Eine Strukturmembervariable wurde als Teil ihrer Deklaration initialisiert.  
  
 **Fehler\-ID:** BC31049  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie eine Konstante anstelle eine Variablen.  
  
-   Fügen Sie der Struktur einen parametrisierten Konstruktor hinzu. Zum Beispiel:  
  
    ```  
    Structure TestStruct Public t As Integer Sub New(ByVal Tval As Integer) t = Tval End Sub End Structure  
    ```  
  
## Siehe auch  
 [How to: Declare a Structure](../Topic/How%20to:%20Declare%20a%20Structure%20\(Visual%20Basic\).md)   
 [Constants and Enumerations](/dotnet/visual-basic/programming-guide/language-features/constants-enums/index)