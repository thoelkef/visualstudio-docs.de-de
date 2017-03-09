---
title: "Compiler Error CS0546 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0546"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0546"
ms.assetid: d259c86f-ee29-4e2d-b381-6ba7252af87e
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compiler Error CS0546
"Accessor": Überschreiben nicht möglich, weil "Eigenschaft" keinen überschreibbaren set\-Accessor hat.  
  
 Beim Versuch, eine der Accessormethoden für eine Eigenschaft zu überschreiben, ist ein Fehler aufgetreten, da der Accessor nicht überschrieben werden kann. Dieser Fehler kann in folgenden Fällen auftreten:  
  
-   Die Basisklasse ist nicht als [virtuell](/dotnet/csharp/language-reference/keywords/virtual) deklariert.  
  
-   Die Basisklasseneigenschaft deklariert den [get](/dotnet/csharp/language-reference/keywords/get)\- oder [set](/dotnet/csharp/language-reference/keywords/set)\-Accessor nicht, den Sie überschreiben möchten.  
  
 Wenn Sie die Basisklasseneigenschaft nicht überschreiben möchten, können Sie vor der Eigenschaft in einer abgeleiteten Klasse das [new](/dotnet/csharp/language-reference/keywords/new)\-Schlüsselwort verwenden.  
  
 Weitere Informationen finden Sie unter [Verwenden von Eigenschaften](/dotnet/csharp/programming-guide/classes-and-structs/using-properties).  
  
## Beispiel  
 Im folgende Beispiel wird CS0546 generiert, da die Basisklasse keinen set\-Accessor für die Eigenschaft deklariert.  
  
```  
// CS0546.cs // compile with: /target:library public class a { public virtual int i { get { return 0; } } public virtual int i2 { get { return 0; } set {} } } public class b : a { public override int i { set {}   // CS0546 error no set } public override int i2 { set {}   // OK } }  
```  
  
## Siehe auch  
 [Eigenschaften](/dotnet/csharp/programming-guide/classes-and-structs/properties)