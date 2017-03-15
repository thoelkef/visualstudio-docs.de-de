---
title: "Compilerfehler CS1562 | Microsoft Docs"
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
  - "CS1562"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1562"
ms.assetid: fbadbcc6-9cf2-4af6-b372-fd4e4da4402e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1562
Für Ausgaben ohne Quelle muss die Option \/out angeben werden.  
  
 Die Kompilierung könnte eine Ausgabedatei erstellt, aber es wurde keine Quellcodedatei als Eingabe verwendet, aus der der Name der Ausgabedatei abgeleitet werden kann. Beispielsweise können Sie versuchen, eine reine Metadaten\- oder reine Ressourcendatei zu kompilieren.  
  
 Verwenden Sie die Compileroption [\/out](/dotnet/csharp/language-reference/compiler-options/out-compiler-option) zum Angeben des Namens der Ausgabedatei.