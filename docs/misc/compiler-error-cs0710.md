---
title: "Compilerfehler CS0710 | Microsoft Docs"
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
  - "CS0710"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0710"
ms.assetid: 753a1a87-f5e5-4758-a960-515069a6c7b0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0710
Statische Klassen können keine Instanzenkonstruktoren haben.  
  
 Eine statische Klasse kann nicht instanziiert werden, daher sind keine Konstruktoren erforderlich. Um diesen Fehler zu vermeiden, entfernen Sie alle Konstruktoren von statischen Klassen, oder legen Sie die Klasse als nicht statisch fest, wenn Sie wirklich Instanzen erstellen möchten.  
  
 Im folgenden Beispiel wird CS0710 generiert:  
  
```  
// CS0710.cs public static class C { public C()  // CS0710 { } public static void Main() { } }  
```