---
title: "Compilerfehler CS0757 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0757"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0757"
ms.assetid: ba093570-306d-4b7b-aad5-1a3855ad6776
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0757
Eine partielle Methode darf nicht über mehrere implementierende Deklarationen verfügen.  
  
 Eine partielle Methode besteht aus genau einer definierenden Deklaration \(Signatur\) und einer oder keiner implementierenden Deklaration \(Text\). Mehrere implementierende Deklarationen für dieselben identischen definierenden Deklarationen sind nicht zulässig. Partielle Methoden können überladen werden, und jede überladene Version kann eine oder keine implementierende Deklaration besitzen.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie für die partielle Methode alle implementierenden Deklarationen bis auf eine.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0757 generiert:  
  
```  
// cs0757.cs using System; public partial class C { // Defining declaration. partial void Part(); // Implementing declaration. partial void Part() { //...Do something. } // Second implementing declaration. partial void Part() // CS0757 { //...Do something. } public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)