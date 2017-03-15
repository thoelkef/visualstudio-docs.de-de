---
title: "Compilerfehler CS0136 | Microsoft Docs"
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
  - "CS0136"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0136"
ms.assetid: 379a1a7d-c52c-4f2b-9e77-c1107d26faf4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0136
Eine lokale Variable mit dem Namen "Var" kann in diesem Bereich nicht deklariert werden, weil "Var" dadurch eine andere Bedeutung erhalten würde, die bereits in einem übergeordneten oder aktuellen\/untergeordneten Bereich in anderer Bedeutung verwendet wird.  
  
 Eine Variablendeklaration blendet eine andere Deklaration aus, die andernfalls im Bereich enthalten wäre. Benennen Sie die Variable um, die in der Zeile deklariert ist, durch die CS0136 generiert wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0136 generiert:  
  
```  
// CS0136.cs  
namespace MyNamespace  
{  
   public class MyClass  
   {  
      public static void Main()  
      {  
         int i = 0;  
         {  
            char i = 'a';   // CS0136, hides int i  
         }  
         i++;  
      }  
   }  
}  
```  
  
 Aus der [C\#\-Sprachspezifikation](/dotnet/csharp/language-reference/language-specification), Abschnitt 7.5.2.1:  
  
 Für jedes Vorkommen eines bestimmten Bezeichners als einfacher Name in einem Ausdruck oder Deklarator innerhalb des lokalen Variablendeklarationsabschnitts \(§3.3\), der dieses Vorkommen unmittelbar einschließt, muss jedes weitere Vorkommen desselben Bezeichners als einfacher Name in einem Ausdruck oder Deklarator auf dieselbe Entität verweisen. Mit dieser Regel wird sichergestellt, dass die Bedeutung eines Namens innerhalb eines bestimmten Blocks, Schalterblocks, einer for\-, foreach\- oder using\-Anweisung oder einer anonymen Funktion immer gleich bleibt.