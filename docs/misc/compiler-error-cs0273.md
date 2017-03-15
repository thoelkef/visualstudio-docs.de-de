---
title: "Compilerfehler CS0273 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0273"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0273"
ms.assetid: 851ad056-feee-48fd-834c-578a1a13e926
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0273
Der Zugriffsmodifizierer des Eigenschaftsaccessor\-Accessors muss restriktiver sein als die Eigenschaft oder der Indexer "Eigenschaft".  
  
 Der Zugriffsmodifizierer des set\/get\-Accessors muss restriktiver sein als die Eigenschaft oder der Indexer "Eigenschaft\/Indexer".  
  
 Dieser Fehler tritt auf, wenn Sie eine Eigenschaft oder einen Indexer mit einem Zugriffsmodifizierer deklarieren, der weniger restriktiv ist als der Zugriffsmodifizierer für einen seiner Accessoren. Um diesen Fehler zu beheben, verwenden Sie den entsprechenden Zugriffsmodifizierer für die Eigenschaft oder den Set\-Accessor. Weitere Informationen finden Sie unter [Accessorzugriff](/dotnet/csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility).  
  
## Beispiel  
 Dieses Beispiel enthält eine interne Eigenschaft mit einer internen set\-Methode. Im folgenden Beispiel wird CS0273 generiert:  
  
```  
// CS0273.cs // compile with: /target:library public class MyClass { internal int Property { get { return 0; } internal set {}   // CS0273 // try the following line instead // private set {} } }  
```