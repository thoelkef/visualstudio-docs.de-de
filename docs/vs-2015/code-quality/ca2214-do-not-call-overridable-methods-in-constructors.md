---
title: 'CA2214: keine über schreibbaren Methoden in Konstruktoren aufzurufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ad467e880b3281a75db2627108af0e0b2f90ea99
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534458"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Überschreibbare Methoden in Konstruktoren nicht aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Der Konstruktor eines nicht versiegelten Typs Ruft eine virtuelle Methode auf, die in der-Klasse definiert ist.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn eine virtuelle Methode aufgerufen wird, wird der tatsächliche Typ, der die Methode ausführt, erst zur Laufzeit ausgewählt. Wenn ein Konstruktor eine virtuelle Methode aufruft, ist es möglich, dass der Konstruktor für die-Instanz, die die-Methode aufruft, nicht ausgeführt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die virtuellen Methoden eines Typs nicht innerhalb der Konstruktoren des Typs abrufen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Der Konstruktor sollte neu gestaltet werden, um den aufzurufenden Befehl der virtuellen Methode auszuschließen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Auswirkung des Verstoßes gegen diese Regel. Die Testanwendung erstellt eine Instanz von `DerivedType` , die bewirkt, dass der Basisklassenkonstruktor ( `BadlyConstructedType` ) ausgeführt wird. `BadlyConstructedType`der Konstruktor ruft fälschlicherweise die virtuelle Methode auf `DoSomething` . Wie die Ausgabe zeigt, wird `DerivedType.DoSomething()` ausgeführt und bewirkt, dass der `DerivedType` Konstruktor ausgeführt wird.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Folgende Ergebnisse werden zurückgegeben:

 Der **basisctor wird aufgerufen.** 
 **Abgeleitetes DoSomething wird als initialisiert bezeichnet? Kein** 
 **Aufruf abgeleiteter ctor.**
