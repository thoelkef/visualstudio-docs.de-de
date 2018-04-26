---
title: 'CA1802: Nach Möglichkeit Literale verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: baa2252b4cdea8312f9d9b309b48604252852b71
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Nach Möglichkeit Literale verwenden
|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Feld wird deklariert `static` und `readonly` (`Shared` und `ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), und wird initialisiert, indem ein Wert, der zur Kompilierungszeit berechnet wird.

## <a name="rule-description"></a>Regelbeschreibung
 Der Wert des einem `static``readonly` Feld wird zur Laufzeit berechnet, wenn der statische Konstruktor für den deklarierenden Typ aufgerufen wird. Wenn die `static``readonly` Feld wird initialisiert, wenn sie deklariert ist, und ein statischer Konstruktor explizit deklariert wird, gibt der Compiler einen statischen Konstruktor aus, um das Feld zu initialisieren.

 Der Wert des eine `const` Feld zur Kompilierungszeit berechnet und gespeichert, die in den Metadaten, wodurch die Leistung zur Laufzeit erhöht wird, Vergleich zu einer `static``readonly` Feld.

 Da es sich bei dem verwendeten Feld zugewiesene Wert zur Kompilierzeit berechnet wird, ändern Sie die Deklaration zu einem `const` Feld, sodass der Wert zur Kompilierzeit statt zur Laufzeit berechnet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen die `static` und `readonly` Modifizierer mit den `const` Modifizierer.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, oder deaktivieren Sie die Regel, wenn die Leistung nicht relevant ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `UseReadOnly`, die die Regel und einen Typ verletzt `UseConstant`, die die Regel erfüllt.

 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]