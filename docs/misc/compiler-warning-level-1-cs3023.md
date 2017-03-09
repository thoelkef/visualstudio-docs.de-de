---
title: "Compilerwarnung (Stufe 1) CS3023 | Microsoft Docs"
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
  - "CS3023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3023"
ms.assetid: fd7782f9-f18a-4ce8-843b-95bf19b54317
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3023
Das CLSCompliant\-Attribut hat keine Bedeutung, wenn es auf die Rückgabetypen angewendet wird.  Versuchen Sie, es stattdessen auf die Methode anzuwenden.  
  
 Rückgabetypen von Funktionen werden nicht auf CLS\-Kompatibilität überprüft, da die CLS\-Kompatibilitätsregeln für Methoden und Typendeklarationen gelten.  
  
## Beispiel  
 Im folgenden Beispiel wird die Warnung CS3023 generiert:  
  
```  
// C3023.cs [assembly:System.CLSCompliant(true)] public class Test { [return:System.CLSCompliant(true)]  // CS3023 // Try this instead: // [method:System.CLSCompliant(true)] public static int Main() { return 0; } }  
```