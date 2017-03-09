---
title: "Compilerwarnung (Stufe 1) CS1695 | Microsoft Docs"
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
  - "CS1695"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1695"
ms.assetid: cc4e4d00-0618-400d-985b-90968e98772c
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1695
Ungültige \#pragma checksum\-Syntax; muss lauten: \#pragma checksum "Dateiname" "{XXXXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXXXXX}" "XXXX..."  
  
 Dieser Fehler sollte selten auftreten, da die Prüfsumme im Allgemeinen zur Laufzeit eingefügt wird, wenn Sie mithilfe der Code\-Dom\-API Code generieren.  
  
 Wenn Sie dann allerdings Eingaben in diese `#pragma`\-Anweisung vornehmen und die GUID oder die Prüfsumme falsch schreiben, würde dieser Fehler ausgegeben. Bei der Syntaxprüfung prüft der Compiler nicht, ob Sie eine korrekte GUID eingegeben haben. Er prüft jedoch, ob die Anzahl der Ziffern und Trennzeichen richtig ist und die Ziffern hexadezimal sind. Ebenso prüft er, ob die Prüfsumme eine gerade Anzahl von Ziffern enthält und die Ziffern hexadezimal sind.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1695 generiert:  
  
```  
// CS1695.cs #pragma checksum "12345"  // CS1695 public class Test { static void Main() { } }  
```