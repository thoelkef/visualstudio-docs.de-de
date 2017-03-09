---
title: "Compilerfehler CS0135 | Microsoft Docs"
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
  - "CS0135"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0135"
ms.assetid: 1bda402c-e8bd-4117-93d9-f4968d9e8303
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0135
'deklaration1' steht im Konflikt mit der Deklaration 'deklaration2'  
  
 Der Compiler lässt das Ausblenden von Namen nicht zu, was häufig zu Logikfehlern im Code führt.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0135 generiert:  
  
```  
// CS0135.cs  
public class MyClass2  
{  
   public static int i = 0;  
  
   public static void Main()  
   {  
      {  
         int i = 4;  
         i++;  
      }  
      i = 0;   // CS0135  
   }  
}  
```  
  
 Aus der [C\#\-Sprachspezifikation](/dotnet/csharp/language-reference/language-specification), Abschnitt 7.5.2.1:  
  
 Für jedes Vorkommen eines bestimmten Bezeichners als einfacher Name in einem Ausdruck oder Deklarator innerhalb des lokalen Variablendeklarationsabschnitts \(§3.3\), der dieses Vorkommen unmittelbar einschließt, muss jedes weitere Vorkommen desselben Bezeichners als einfacher Name in einem Ausdruck oder Deklarator auf dieselbe Entität verweisen. Mit dieser Regel wird sichergestellt, dass die Bedeutung eines Namens innerhalb eines bestimmten Blocks, Schalterblocks, einer for\-, foreach\- oder using\-Anweisung oder einer anonymen Funktion immer gleich bleibt.