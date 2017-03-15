---
title: "Compilerfehler CS1666 | Microsoft Docs"
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
  - "CS1666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1666"
ms.assetid: 4d62aa9c-71b9-4c6e-8141-2426d20ac243
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1666
Sie können keine Puffer fester Größe in ungebundenen Ausdrücken verwenden. Verwenden Sie die fixed\-Anweisung.  
  
 Dieser Fehler tritt auf, wenn Sie einen Puffer mit fester Größe in einem Ausdruck mit einer Klasse verwenden, die selbst nicht fest ist. Die Laufzeit kann die ungebundene Klasse verschieben, um den Speicherzugriff zu optimieren, was jedoch bei Verwendung eines Puffers fester Größe zu Fehlern führen kann. Um diesen Fehler zu vermeiden, verwenden Sie das `fixed`\-Schlüsselwort für die Anweisung.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1666 generiert:  
  
```  
// CS1666.cs // compile with: /unsafe /target:library unsafe struct S { public fixed int buffer[1]; } unsafe class Test { S field = new S(); private bool example1() { return (field.buffer[0] == 0);   // CS1666 error } private bool example2() { // OK fixed (S* p = &field) { return (p->buffer[0] == 0); } } private bool example3() { S local = new S(); return (local.buffer[0] == 0); } }  
```