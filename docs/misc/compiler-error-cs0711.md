---
title: "Compilerfehler CS0711 | Microsoft Docs"
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
  - "CS0711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0711"
ms.assetid: 3a5a6d90-e15d-4808-a7a6-c85fd011a0d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0711
Statische Klassen können keine Destruktoren enthalten.  
  
 Eine statische Klasse kann nicht instanziiert werden, daher sind keine Konstruktoren oder Destruktoren erforderlich. Um diesen Fehler zu vermeiden, entfernen Sie alle Destruktoren von statischen Klassen, oder legen Sie die Klasse als nicht statisch fest, wenn Sie wirklich Instanzen erstellen und löschen möchten.  
  
 Im folgenden Beispiel wird CS0711 generiert:  
  
```  
// CS0711.cs public static class C { ~C()  // CS0711 { } public static void Main() { } }  
```