---
title: "CA2207: Statische Felder f&#252;r Werttyp inline initialisieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeValueTypeStaticFieldsInline"
  - "CA2207"
helpviewer_keywords: 
  - "CA2207"
  - "InitializeValueTypeStaticFieldsInline"
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2207: Statische Felder f&#252;r Werttyp inline initialisieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Werttyp deklariert einen expliziten statischen Konstruktor.  
  
## Regelbeschreibung  
 Ein Werttyp wird bei der Deklaration standardmäßig initialisiert. Dabei werden alle Werttypfelder auf 0 \(null\) festgelegt und alle Verweistypfelder auf `null` \(`Nothing` in Visual Basic\).  Ein expliziter statischer Konstruktor wird nur vor dem Aufruf von Instanzenkonstruktoren oder statischen Membern des Typs garantiert ausgeführt.  Wenn Sie also einen Typ ohne Aufruf eines Instanzenkonstruktors erstellen, ist nicht garantiert, dass der statische Konstruktor ausgeführt wird.  
  
 Wenn alle statischen Daten inline initialisiert werden und kein expliziter statischer Konstruktor deklariert wird, fügen der Compiler von C\# und der Compiler von Visual Basic der MSIL\-Klassendefinition die `beforefieldinit`\-Flag hinzu.  Die Compiler fügen auch einen privaten statischen Konstruktor hinzu, der den statischen Initialisierungscode enthält.  Dieser private statische Konstruktor wird garantiert vor dem Zugriff auf statische Felder des Typs ausgeführt.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Verwandte Regeln  
 [CA1810: Statische Felder von Verweistypen inline initialisieren](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)