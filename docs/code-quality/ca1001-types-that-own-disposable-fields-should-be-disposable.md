---
title: "CA1001: Typen, die l&#246;schbare Felder besitzen, m&#252;ssen gel&#246;scht werden k&#246;nnen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1001"
  - "TypesThatOwnDisposableFieldsShouldBeDisposable"
helpviewer_keywords: 
  - "CA1001"
  - "TypesThatOwnDisposableFieldsShouldBeDisposable"
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1001: Typen, die l&#246;schbare Felder besitzen, m&#252;ssen gel&#246;scht werden k&#246;nnen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der Typ nicht außerhalb der Assembly sichtbar ist.<br /><br /> Unterbrechend – Wenn der Typ außerhalb der Assembly sichtbar ist.|  
  
## Ursache  
 Eine Klasse deklariert und implementiert ein Instanzenfeld, das den <xref:System.IDisposable?displayProperty=fullName>\-Typ aufweist, implementiert jedoch <xref:System.IDisposable> nicht.  
  
## Regelbeschreibung  
 Eine Klasse implementiert die <xref:System.IDisposable>\-Schnittstelle, um nicht verwaltete Ressourcen, die sie besitzt, zu entfernen.  Ein Instanzenfeld, das den <xref:System.IDisposable>\-Typ aufweist, gibt an, dass das Feld eine nicht verwaltete Ressource besitzt.  Eine Klasse, die ein <xref:System.IDisposable>\-Feld deklariert, besitzt indirekt eine nicht verwaltete Ressource und sollte die <xref:System.IDisposable>\-Schnittstelle implementieren.  Wenn die Klasse keine nicht verwalteten Ressourcen direkt besitzt, sollte sie keinen Finalizer implementieren.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie <xref:System.IDisposable>, und rufen Sie in der <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>\-Methode die <xref:System.IDisposable.Dispose%2A>\-Methode des Felds auf.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Klasse, die gegen die Regel verstößt, und eine Klasse, die der Regel durch die Implementierung von <xref:System.IDisposable> entspricht.  Die Klasse implementiert keinen Finalizer, da sie direkt keine nicht verwalteten Ressourcen besitzt.  
  
 [!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
 [!code-cs[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]  
  
## Verwandte Regeln  
 [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Dispose\-Methoden müssen die Dispose\-Funktion der Basisklasse aufrufen](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)