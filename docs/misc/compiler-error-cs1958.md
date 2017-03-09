---
title: "Compilerfehler CS1958 | Microsoft Docs"
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
  - "CS1958"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1958"
ms.assetid: bb6f3bb2-ea93-4d2e-984c-da9c99f5653f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1958
Objekt\- und Auflistungsinitialisiererausdrücke dürfen nicht auf Delegaterstellungsausdrücke angewendet werden.  
  
 Ein Delegat besitzt anders als Klassen oder Strukturen keine Member, daher gibt es für einen Objektinitialisierer nichts zu initialisieren. Wenn dieser Fehler auftritt, liegt es wahrscheinlich daran, dass hinter dem Delegaterstellungsausdruck geschweifte Klammern folgen. Entfernen Sie einfach die geschweiften Klammern, damit dieser Fehler nicht mehr angezeigt wird.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die geschweiften Klammern.  
  
## Beispiel  
 Mit dem folgenden Code wird CS1958 generiert:  
  
```  
// cs1958.cs public class MemberInitializerTest { delegate void D<T>(); public static void GenericMethod<T>() { } public static void Run() { D<int> genD = new D<int>(GenericMethod<int>) { }; // CS1958 // Try the following line instead // D<int> genD = new D<int>(GenericMethod<int>); } }  
```