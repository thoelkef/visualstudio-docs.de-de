---
title: "Compilerfehler CS0764 | Microsoft Docs"
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
  - "CS0764"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0764"
ms.assetid: 76a64149-49d8-40ea-a976-03835d8fb7eb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0764
Beide partiellen Methodendeklarationen müssen unsicher sein, oder keine von beiden darf unsicher sein.  
  
 Eine partielle Methode besteht aus einer definierenden Deklaration \(Signatur\) und einer optionalen implementierenden Deklaration \(Text\). Wenn die definierende Deklaration den `unsafe`\-Modifizierer aufweist, muss auch die implementierende Deklaration darüber verfügen. Umgekehrt gilt, wenn die implementierende Deklaration über den `unsafe`\-Modifizierer verfügt, muss auch die definierende Deklaration darüber verfügen.  
  
### So beheben Sie diesen Fehler  
  
1.  Vorausgesetzt, dass die definierende Deklaration korrekt ist, fügen Sie den `unsafe`\-Modifizierer der implementierenden Deklaration hinzu bzw. entfernen Sie diesen daraus, sodass sie mit der definierenden Deklaration übereinstimmt.  
  
## Beispiel  
  
```  
// cs0764.cs //  Compile with: /target:library /unsafe public partial class C { partial void Part(); unsafe partial void Part() //CS0764 { } public static int Main() { return 1; } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)