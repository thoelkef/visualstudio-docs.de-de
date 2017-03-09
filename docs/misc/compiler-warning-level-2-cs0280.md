---
title: "Compilerwarnung (Stufe 2) CS0280 | Microsoft Docs"
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
  - "CS0280"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0280"
ms.assetid: 9b453478-92aa-4fd2-9b87-780fd138603a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0280
"Typ" implementiert das Muster "Mustername" nicht. "Methodenname" weist die falsche Signatur auf.  
  
 Die beiden C\#\-Anweisungen **foreach** und **using** basieren auf den vordefinierten Mustern "Auflistung" und "Ressource". Diese Warnung tritt auf, wenn der Compiler eine dieser Anweisungen aufgrund einer falschen Methodensignatur nicht ihrem Muster zuordnen kann. Das Muster "Auflistung" erfordert z. B. eine Methode namens <xref:System.Collections.IEnumerator.MoveNext%2A>, die keine Parameter akzeptiert und einen `boolean`\-Wert zurückgibt. Der Code kann eine <xref:System.Collections.IEnumerator.MoveNext%2A>\-Methode enthalten, die über einen Parameter verfügt oder ggf. ein Objekt zurückgibt.  
  
 Das Muster "Ressource" und `using` liefern ein weiteres Beispiel. Das Muster "Ressource" erfordert die <xref:System.IDisposable.Dispose%2A>\-Methode. Wenn Sie eine gleichnamige Eigenschaft definieren, erhalten Sie diese Warnung.  
  
 Um den Fehler zu beheben, stellen Sie sicher, dass die Methodensignaturen Ihres Typs mit den Signaturen der entsprechenden Methoden im Muster übereinstimmen. Außerdem dürfen keine Eigenschaften mit dem gleichen Namen wie eine Methode vorhanden sein, die vom Muster benötigt wird.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0280 generiert.  
  
```  
// CS0280.cs using System; using System.Collections; public class ValidBase: IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } } class Derived : ValidBase { // field, not method new public int GetEnumerator; } public class Test { public static void Main() { foreach (int i in new Derived()) {}   // CS0280 } }  
```