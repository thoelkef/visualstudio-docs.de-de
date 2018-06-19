---
title: 'CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5ebcd4164f9db28d4cb1f150ee3a4bb21b21cde
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920110"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen
|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Der Konstruktor eines nicht versiegelten Typs Ruft eine virtuelle Methode in der Klasse definiert.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn eine virtuelle Methode aufgerufen wird, ist der tatsächliche Typ, der die Methode ausgeführt wird, nicht bis zur Laufzeit ausgewählt. Wenn ein Konstruktor eine virtuelle Methode aufruft, ist es möglich, dass der Konstruktor für die Instanz, die die Methode aufruft, nicht ausgeführt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie nicht virtuelle Methoden des Typs mithilfe der Konstruktoren des Typs.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Der Konstruktor sollte neu gestaltet werden, um den Aufruf der virtuellen Methode zu vermeiden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht den Effekt der Verstoß gegen diese Regel. Die Anwendung zu testen, erstellt eine Instanz des `DerivedType`, dies bedeutet, dass ihre Basisklasse (`BadlyConstructedType`) Konstruktor ausgeführt. `BadlyConstructedType`der Konstruktor ruft falsch virtuelle Methode `DoSomething`. Wie die Ausgabe zeigt, `DerivedType.DoSomething()` ausgeführt wird, und gilt für sollten Sie vor dem `DerivedType`Konstruktor führt.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/CSharp/ca2214-do-not-call-overridable-methods-in-constructors_1.cs)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../code-quality/codesnippet/VisualBasic/ca2214-do-not-call-overridable-methods-in-constructors_1.vb)]

 Folgende Ergebnisse werden zurückgegeben:

 **Aufrufen des Basiskonstruktors. ** 
 **Abgeleitete DoSomething heißt - initialisiert? Nicht**
**aufrufen abgeleiteten Ctor.**