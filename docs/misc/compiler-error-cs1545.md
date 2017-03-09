---
title: "Compilerfehler CS1545 | Microsoft Docs"
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
  - "CS1545"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1545"
ms.assetid: 56c377b5-4cf1-4c7d-b51d-463bad78f3ef
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1545
Die Eigenschaft, der Indexer oder das Ereignis "Eigenschaft" wird von der Sprache nicht unterstützt. Rufen Sie die Accessormethode "set\-Accessor" oder "get\-Accessor" direkt auf.  
  
 Der Code nutzt ein Objekt, das einen nicht standardmäßigen [Indexer](/dotnet/csharp/programming-guide/indexers/index) hat, und versucht, die indizierte Syntax zu verwenden. Um diesen Fehler zu beheben, rufen Sie die `get`\- oder `set`\-Accessormethode der Eigenschaft auf.  
  
## Beispiel  
  
```  
// CPP1545.cpp // compile with: /clr /LD // a Visual C++ program using namespace System; public ref struct Employee { Employee( String^ s, int d ) {} property String^ name { String^ get() { return nullptr; } } }; public ref struct Manager { property Employee^ Report [String^] { Employee^ get(String^ s) { return nullptr; } void set(String^ s, Employee^ e) {} } };  
```  
  
## Beispiel  
 Im folgenden Beispiel wird CS1545 generiert:  
  
```  
// CS1545.cs // compile with: /r:CPP1545.dll class x { public static void Main() { Manager Ed = new Manager(); Employee Bob = new Employee("Bob Smith", 12); Ed.Report[ Bob.name ] = Bob;   // CS1545 Ed.set_Report( Bob.name, Bob);   // OK } }  
```