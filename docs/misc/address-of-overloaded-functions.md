---
title: "Adresse von &#252;berladenen Funktionen | Microsoft Docs"
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
  - "Adressen [C++], überladene Funktionen"
  - "Adressen [C++], Zurückgeben von überladenen"
  - "Funktion überladen, Funktionsadresse"
  - "this-Zeiger, überladene Funktionen"
ms.assetid: e7913e65-a295-445d-b2b0-1e60f8dfbc54
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Adresse von &#252;berladenen Funktionen
Durch Verwendung eines Funktionsnamens ohne Argumente wird die Adresse dieser Funktion zurückgegeben. Zum Beispiel:  
  
```  
int Func( int i, int j );  
int Func( long l );  
  
...  
  
int (*pFunc) ( int, int ) = Func;  
```  
  
 Im vorhergehenden Beispiel wird die erste Version von `Func` ausgewählt, und die entsprechende Adresse wird in `pFunc` kopiert.  
  
 Der Compiler bestimmt, welche Version der Funktion ausgewählt wird, indem er eine Funktion mit einer Argumentliste sucht, die exakt mit der des Ziels übereinstimmt. Die Argumente in den Deklarationen der überladenen Funktionen werden mit Folgendem abgeglichen:  
  
-   Einem Objekt, das initialisiert wird \(wie im vorherigen Beispiel gezeigt\)  
  
-   Der linken Seite einer Zuweisungsanweisung  
  
-   Einem formalen Argument für eine Funktion  
  
-   Einem formalen Argument für einen benutzerdefinierten Operator  
  
-   Einem Funktionsrückgabetyp  
  
 Wenn keine genaue Übereinstimmung gefunden wird, ist der Ausdruck für die Adresse der Funktion mehrdeutig, und es wird ein Fehler ausgelöst.  
  
 Beachten Sie, dass obwohl im vorherigen Beispiel eine Nichtmemberfunktion, `Func`, verwendet wurde, die gleichen Regeln angewendet werden, wenn die Adresse von überladenen Memberfunktionen akzeptiert wird.  
  
## Siehe auch  
 [Überladen \(C\+\+\)](../misc/overloading-cpp.md)