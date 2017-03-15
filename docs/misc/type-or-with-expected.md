---
title: "Typ oder &#39;With&#39; erwartet | Microsoft Docs"
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
  - "vbc30988"
  - "bc30988"
helpviewer_keywords: 
  - "BC30988"
ms.assetid: ab9c0cee-9fe4-4764-a3c2-aec16e709d4c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typ oder &#39;With&#39; erwartet
Wenn Sie eine Instanz einer Klasse deklarieren, muss auf das Schlüsselwort `New` ein Typname oder `With` folgen. Die folgenden Anweisungen deklarieren z. B. jeweils, dass `client` eine Instanz der `Customer`\-Klasse ist. Der Typname `Customer` folgt auf `New`.  
  
```  
' Dim client As New Customer()  
' The next declaration uses an object initializer.  
Dim client As New Customer() With {.Name = "Litware, Inc."}  
```  
  
 Beginnend mit [!INCLUDE[vb_orcas_long](../misc/includes/vb_orcas_long_md.md)] können Sie ein Objekt als eine Instanz eines anonymen Typs deklarieren. In diesem Fall geben Sie keinen Datentyp an. In Deklarationen anonymer Typen folgt das Schlüsselwort `With` auf `New`.  
  
```  
Dim person = New With {.Name ="Mike Nash", .Age = 27}  
```  
  
 **Fehler\-ID:** BC30988  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Deklaration so, dass `With` oder ein Typname auf `New` folgt.  
  
## Siehe auch  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [NotInBuild: Deklarationsanweisungen in Visual Basic](http://msdn.microsoft.com/de-de/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)