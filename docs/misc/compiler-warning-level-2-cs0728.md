---
title: "Compilerwarnung (Stufe 2) CS0728 | Microsoft Docs"
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
  - "CS0728"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0728"
ms.assetid: ad6d860d-bac4-48f3-9eab-1efd2b6de6c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0728
Möglicherweise falsche Zuweisung zur lokalen 'variable', die das Argument zu einer using\- oder lock\-Anweisung ist.  Der Aufruf von 'Dispose' oder Entsperren treten beim ursprünglichen Wert der lokalen Variablen ein.  
  
 Es gibt eine Reihe von Szenarien, in denen `using`\- oder `lock`\-Blöcke zu einem zeitweiligen Ressourcenverlust führen. Es folgt ein Beispiel:  
  
 `thisType f = null;`  
  
 `using (f)`  
  
 `{`  
  
 `f = new thisType();`  
  
 `...`  
  
 `}`  
  
 In diesen Fall wird der ursprüngliche Wert der Variablen `thisType`, wie etwa null, verworfen, wenn die Ausführung des `using`\-Blocks abgeschlossen ist, das `thisType`\-Objekt, das innerhalb des Blocks erstellt wurde, jedoch nicht; allerdings fällt es möglicherweise der Garbage Collection zum Opfer.  
  
 Verwenden Sie die folgende Form, um diesen Fehler zu beheben:  
  
 `using (thisType f = new thisType())`  
  
 `{`  
  
 `...`  
  
 `}`  
  
 In diesem Fall wird das neu zugewiesene `thisType`\-Objekt verworfen.  
  
## Beispiel  
 Im folgenden Code wird die Warnung CS0728 generiert.  
  
```  
// CS0728.cs using System; public class ValidBase : IDisposable { public void Dispose() {  } } public class Logger { public static void dummy() { ValidBase vb = null; using (vb) { vb = null;  // CS0728 } vb = null; } public static void Main() { } }  
```