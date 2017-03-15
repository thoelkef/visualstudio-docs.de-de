---
title: "Compilerfehler CS0434 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0434"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0434"
ms.assetid: 8f8871fc-a4bb-4a9e-ba19-999f4943001e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0434
Der Namespace 'NamespaceName1' in 'NamespaceName2' steht in Konflikt mit dem Typ 'Typname1' in 'Namespacename3'  
  
 Dieser Fehler tritt auf, wenn ein importierter Typ und ein importierter geschachtelter Namespace den gleichen vollqualifizierten Namen aufweisen. Wenn auf diesen Namen verwiesen wird, kann der Compiler nicht zwischen den beiden unterscheiden. Wenn Sie den importierten Quellcode ändern können, können Sie den Fehler beheben, indem Sie den Namen entweder des Typs oder des Namespaces ändern, so dass beide innerhalb der Assembly eindeutig sind.  
  
 Durch den folgenden Code wird der Fehler CS0434 ausgelöst.  
  
## Beispiel  
 Dieser Code erstellt die erste Kopie des Typs mit dem identischen vollqualifizierten Namen.  
  
```  
// CS0434_1.cs // compile with: /t:library namespace TypeBindConflicts { namespace NsImpAggPubImp { public class X { } } }  
```  
  
## Beispiel  
 Dieser Code erstellt die zweite Kopie des Typs mit dem identischen vollqualifizierten Namen.  
  
```  
// CS0434_2.cs // compile with: /t:library namespace TypeBindConflicts { // Conflicts with another import (import2.cs). public class NsImpAggPubImp { } // Try this instead: // public class UniqueClassName { } }  
```  
  
## Beispiel  
 Dieser Code verweist auf den Typ mit dem identischen vollqualifizierten Namen.  
  
```  
// CS0434.cs // compile with: /r:cs0434_1.dll /r:cs0434_2.dll using TypeBindConflicts; public class Test { public TypeBindConflicts.NsImpAggPubImp.X n2 = null; // CS0434 }  
```