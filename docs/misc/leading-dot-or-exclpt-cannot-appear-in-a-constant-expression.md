---
title: "In einem Konstantenausdruck k&#246;nnen keine vorangestellten &#39;.&#39; oder &#39;!&#39; verwendet werden. | Microsoft Docs"
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
  - "vbc30995"
  - "bc30995"
helpviewer_keywords: 
  - "BC30995"
ms.assetid: eed62684-66db-4fdb-9da7-f1407a55b172
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# In einem Konstantenausdruck k&#246;nnen keine vorangestellten &#39;.&#39; oder &#39;!&#39; verwendet werden.
Memberzugriff \(.\) und Wörterbuchmemberzugriff \(\!\) erfordern einen Ausdruck, der das Element angibt, das den Member größtenteils enthält, einschließlich der Konstantenausdrücke. Die folgende Deklaration ist ungültig.  
  
```  
' Not valid. Const c As String = .name  
```  
  
 **Fehler\-ID:** BC30995  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie die Instanz an, die den Member enthält, auf den Sie zugreifen möchten.  
  
## Siehe auch  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Gewusst wie: Deklarieren einer Instanz eines anonymen Typs \(Visual Basic\)](http://msdn.microsoft.com/de-de/119f616c-9bcd-4731-ac00-4285be5959f7)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)