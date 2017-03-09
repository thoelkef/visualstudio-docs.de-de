---
title: "Compilerfehler CS0554 | Microsoft Docs"
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
  - "CS0554"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0554"
ms.assetid: 884db4b2-3a69-4434-9a25-526f596e03c8
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0554
"Konvertierungsroutine": benutzerdefinierte Konvertierung zu\/von der abgeleiteten Klasse  
  
 Benutzerdefinierte Konvertierungen in Werte einer abgeleiteten Klasse sind nicht zulässig. Ein solcher Operator ist nicht erforderlich.  
  
 Weitere Informationen zu benutzerdefinierten Konvertierungen finden Sie im Kapitel 6 in der C\#\-Sprachspezifikation.  
  
 Im folgenden Beispiel wird CS0554 generiert:  
  
```  
// CS0554.cs namespace x { public class ii { // delete the conversion routine to resolve CS0554 public static implicit operator ii(a aa) // CS0554 { return new ii(); } } public class a : ii { public static void Main() { } } }  
```