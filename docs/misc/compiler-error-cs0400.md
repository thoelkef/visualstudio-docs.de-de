---
title: "Compilerfehler CS0400 | Microsoft Docs"
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
  - "CS0400"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0400"
ms.assetid: 58f91f3b-30f4-433b-9a13-0cff258a2630
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0400
Der Typ\- oder Namespacename 'identifier' konnte im globalen Namespace nicht gefunden werden. \(Fehlt ein Assemblyverweis?\)  
  
 Der Bezeichner, für den der globale Bereichsoperator angegeben wurde \(`::`\), wurde nicht im globalen Namespace gefunden. Möglicherweise fehlt ein Assemblyverweis, der den Bezeichner enthält, oder der Bezeichner wurde in einer Klasse oder einem Namespace deklariert, der bzw. die nicht dem globalen Namespace angehört. Dieser Fehler kann auch auftreten, wenn ein global gültiger Bezeichner nicht deklariert oder falsch geschrieben wurde.  
  
 Um diesen Fehler zu vermeiden, suchen Sie die Deklaration des Bezeichners, überprüfen Sie die richtige Schreibung, und, wenn die Deklaration sich in einer separaten Assembly befindet, stellen Sie sicher, dass Sie den passenden Assemblyverweis verwenden. Wenn der Bezeichner in einem anderen Typ oder Namespace deklariert ist, verwenden Sie hinter dem '::' den vollqualifizierten Namen. Im folgenden Beispiel wird CS0400 generiert:  
  
```  
// CS0400.cs class C { public static void Main() { // CS0400 - D could not be found // in the global namespace. global::D d = new global::D(); } }  
```