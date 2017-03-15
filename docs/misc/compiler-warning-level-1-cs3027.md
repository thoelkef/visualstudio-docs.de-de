---
title: "Compilerwarnung (Stufe 1) CS3027 | Microsoft Docs"
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
  - "CS3027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3027"
ms.assetid: c515e623-3f5a-49fa-a878-f1d8e90fdc24
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3027
"Typ\_1" ist nicht CLS\-kompatibel, da die Basisschnittstelle "Typ\_2" nicht CLS\-kompatibel ist  
  
 Ein nicht CLS\-kompatibler Typ kann nicht als Basistyp für einen CLS\-kompatiblen Typ verwendet werden.  
  
## Beispiel  
 Das folgende Beispiel enthält eine Schnittstelle mit einer Methode, in deren Signatur ein nicht CLS\-kompatibler Typ verwendet wird, wodurch der Typ nicht CLS\-kompatibel wird.  
  
```  
// CS3027.cs // compile with: /target:library public interface IBase { void IMethod(uint i); }  
```  
  
## Beispiel  
 Im folgenden Beispiel wird CS3027 generiert.  
  
```  
// CS3027_b.cs // compile with: /reference:CS3027.dll /target:library /W:1 [assembly:System.CLSCompliant(true)] public interface IDerived : IBase {}  
```