---
title: "CA1810: Statische Felder von Verweistypen inline initialisieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
helpviewer_keywords: 
  - "InitializeReferenceTypeStaticFieldsInline"
  - "CA1810"
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1810: Statische Felder von Verweistypen inline initialisieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeReferenceTypeStaticFieldsInline|  
|CheckId|CA1810|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Verweistyp deklariert einen expliziten statischen Konstruktor.  
  
## Regelbeschreibung  
 Wenn ein Typ einen expliziten statischen Konstruktor deklariert, überprüft der JIT\-Compiler \(Just in Time\) jede statische Methode und jeden Instanzenkonstruktor des Typs. Dadurch wird sichergestellt, dass der statische Konstruktor zuvor aufgerufen wurde.  Die statische Initialisierung wird ausgelöst, wenn auf einen statischen Member zugegriffen wird oder wenn eine Instanz des Typs erstellt wird.  Die statische Initialisierung wird allerdings nicht ausgelöst, wenn eine Variable des Typs zwar deklariert, aber nicht verwendet wird. Die Nichtverwendung kann von großer Bedeutung sein, wenn durch die Initialisierung der globale Zustand verändert wird.  
  
 Wenn alle statischen Daten inline initialisiert werden und kein expliziter statischer Konstruktor deklariert wird, fügen MSIL\-\(Microsoft Intermediate Language\-\)Compiler die `beforefieldinit`\-Flag und einen impliziten statischen Konstruktor hinzu, welcher die statischen Daten gemäß der MSIL\-Typdefinition initialisiert.  Wenn der JIT\-Compiler auf die `beforefieldinit`\-Flag trifft, werden meist keine zusätzlichen Konstruktorüberprüfungen durchgeführt.  Die statische Initialisierung wird auf jeden Fall vor dem Zugriff auf die statischen Felder durchgeführt, aber erst nachdem eine statische Methode\/ein Instanzenkonstruktor aufgerufen wurde.  Die statische Initialisierung kann zu jedem Zeitpunkt nach der Deklarierung einer Typvariablen durchgeführt werden.  
  
 Durch die Überprüfung statischer Konstruktoren kann die Leistung herabgesetzt werden.  Häufig werden statische Konstruktoren ausschließlich zur Initialisierung statischer Felder verwendet. In diesen Fällen ist lediglich zu beachten, dass die statische Initialisierung vor dem ersten Zugriff auf das statische Feld erfolgen muss.  Das `beforefieldinit`\-Verhalten ist für diese und die meisten anderen Typen geeignet.  Es ist nur dann ungeeignet, wenn durch die statische Initialisierung der globale Zustand beeinflusst wird, und eine der folgenden Aussagen zutrifft:  
  
-   Die Auswirkung auf den globalen Zustand ist mit hohen Kosten verbunden und ist nicht erforderlich, wenn der Typ nicht verwendet wird.  
  
-   Der Zugriff auf die Auswirkungen auf den globalen Zustand kann ohne gleichzeitigen Zugriff auf irgendeines der statischen Felder des Typs erfolgen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, initialisieren Sie alle statischen Daten nach deren Deklaration und entfernen den statischen Konstruktor.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann in folgenden Fällen gefahrlos unterdrückt werden: Die Leistung ist kein Kriterium; die Änderungen des globalen Zustands aufgrund der statischen Initialisierung verursachen hohe Kosten; die Änderungen des globalen Zustands müssen auf jeden Fall erfolgen, bevor eine statische Methode des Typs aufgerufen oder eine Instanz des Typs erstellt wird.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ gezeigt, der gegen die Regel verstößt \(`StaticConstructor`\), und ein Typ, der den statischen Konstruktor zwecks Regelkonformität durch eine Inlineinitialisierung ersetzt \(`NoStaticConstructor`\).  
  
 [!code-cs[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/CSharp/ca1810-initialize-reference-type-static-fields-inline_1.cs)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../code-quality/codesnippet/VisualBasic/ca1810-initialize-reference-type-static-fields-inline_1.vb)]  
  
 Beachten Sie die hinzugefügte `beforefieldinit`\-Flag auf der MSIL\-Definition der `NoStaticConstructor`\-Klasse.  
  
  **.class public auto ansi StaticConstructor**  
 **extends \[mscorlib\]System.Object**  
**{**  
**} \/\/ Ende der Klasse StaticConstructor**  
**.class public auto ansi beforefieldinit NoStaticConstructor**  
 **extends \[mscorlib\]System.Object**  
**{**  
**} \/\/ Ende der Klasse NoStaticConstructor**   
## Verwandte Regeln  
 [CA2207: Statische Felder für Werttyp inline initialisieren](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)