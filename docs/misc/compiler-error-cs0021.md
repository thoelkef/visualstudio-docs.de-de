---
title: "Compilerfehler CS0021 | Microsoft Docs"
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
  - "CS0021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0021"
ms.assetid: 4eb5fa24-8261-4962-b36a-224be5074217
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0021
Eine Indizierung mit \[\] kann nicht auf einen Ausdruck vom Typ „type“ angewendet werden.  
  
 Es wurde versucht, auf einen Wert über einen Indexer für einen Datentyp zuzugreifen, der [Indexer](/dotnet/csharp/programming-guide/indexers/index) nicht unterstützt.  
  
 Wenn Sie versuchen, einen Indexer in einer C\+\+\-Assembly zu verwenden, erhalten Sie möglicherweise den Fehler CS0021. In diesem Fall ergänzen Sie die C\+\+\-Klasse mit dem `DefaultMember`\-Attribut, damit der C\#\-Compiler weiß, welcher Indexer standardmäßig verwendet wird. Im folgenden Beispiel wird CS0021 generiert:  
  
## Beispiel  
 Diese Datei wird in eine DLL\-Datei kompiliert. Dabei wurde das `DefaultMember`\-Attribut auskommentiert, um den Fehler zu generieren.  
  
```  
// CPP0021.cpp // compile with: /clr /LD using namespace System::Reflection; // Uncomment the following line to resolve //[DefaultMember("myItem")] public ref class MyClassMC { public: property int myItem[int] { int get(int i){  return 5; } void set(int i, int value) {} } };  
```  
  
## Beispiel  
 Im folgenden ist die C\#\-Datei dargestellt, die die DLL\-Datei aufruft. Diese Datei versucht, auf die Klasse über einen Indexer zuzugreifen, da aber kein Member als Standardindexer deklariert wurde, wird der Fehler generiert.  
  
```  
// CS0021.cs // compile with: /reference:CPP0021.dll public class MyClass { public static void Main() { MyClassMC myMC = new MyClassMC(); int j = myMC[1]; // CS0021 } }  
```