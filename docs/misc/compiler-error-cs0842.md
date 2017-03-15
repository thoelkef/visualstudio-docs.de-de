---
title: "Compilerfehler CS0842 | Microsoft Docs"
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
  - "CS0842"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0842"
ms.assetid: 93a8b333-efc4-40c7-ae53-5264f721a74f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0842
Automatisch implementierte Eigenschaften können nicht in einem Typ verwendet werden, der mit 'StructLayout\(LayoutKind.Explicit\)' markiert ist.  
  
 Die Unterstützungsfelder von automatisch implementierten Eigenschaften werden vom Compiler zur Verfügung gestellt und sind für Quellcode nicht zugänglich. Daher sind sie mit <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> nicht kompatibel.  
  
### So beheben Sie diesen Fehler  
  
1.  Machen Sie die Eigenschaft zu einer gewöhnlichen Eigenschaft, für die Sie den Text der Zugriffsmethoden angeben.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0842 generiert:  
  
```  
// cs0842.cs using System; using System.Runtime.InteropServices; namespace TestNamespace { [StructLayout(LayoutKind.Explicit)] struct Str { public int Num // CS0842 { get; set; } static int Main() { return 1; } } }  
```