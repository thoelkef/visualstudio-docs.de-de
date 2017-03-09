---
title: "&#220;bersicht &#252;ber &#220;berladen | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funktionsüberladung, Informationen über die funktionsüberladung"
  - "überladen zum Überladen von Operatoren"
ms.assetid: cd012dd4-607c-4f8e-bd2e-2bd506ac81ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &#220;bersicht &#252;ber &#220;berladen
Mit der Programmiersprache C\+\+ können Sie Funktionen und Operatoren überladen. Als Überladung wird die Bereitstellung von mehreren Definitionen für einen bestimmten Funktionsnamen in demselben Bereich bezeichnet. Der Compiler muss die entsprechende Version der Funktion oder des Operators anhand der Argumente auswählen, mit denen er aufgerufen wird. Zum Beispiel gilt die Funktion "max" als überladene Funktion. Die Verwendung erfolgt in Code wie beispielsweise:  
  
```  
// overview_overload.cpp  
double max( double d1, double d2 )  
{  
   return ( d1 > d2 ) ? d1 : d2;  
}  
  
int max( int i1, int i2 )  
{  
   return ( i1 > i2 ) ? i1 : i2;  
}  
int main()  
{  
   int    i = max( 12, 8 );  
   double d = max( 32.9, 17.4 );  
}  
```  
  
 Im ersten Funktionsaufruf, in dem der maximale Wert von zwei Variablen des Typs `int` angefordert wird, wird die Funktion `max( int, int )` aufgerufen. Allerdings sind im zweiten Funktionsaufruf die Argumente vom Typ `double`, sodass die Funktion `max( double, double )` aufgerufen wird.  
  
## Siehe auch  
 [Überladen \(C\+\+\)](../misc/overloading-cpp.md)