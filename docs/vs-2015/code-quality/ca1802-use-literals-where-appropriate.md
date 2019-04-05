---
title: 'CA1802: Nach Möglichkeit Literale verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5990d8ea3720098651d3ed696f6ee5ff907b82f3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946800"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Nach Möglichkeit Literale verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Feld ist deklariert `static` und `readonly` (`Shared` und `ReadOnly` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), und mit einem Wert, der zum Zeitpunkt der Kompilierung zu berechnendes ist initialisiert wird.

## <a name="rule-description"></a>Regelbeschreibung
 Der Wert des einem `static``readonly` Feld wird zur Laufzeit berechnet, wenn der statische Konstruktor für den deklarierenden Typ aufgerufen wird. Wenn die `static``readonly` Feld initialisiert wird, wenn sie deklariert wurde und ein statischer Konstruktor explizit deklariert wird, gibt der Compiler einen statischen Konstruktor zum Initialisieren des Felds.

 Der Wert des einem `const` Feld wird zur Kompilierungszeit berechnet und in der Metadaten, die Leistung zur Laufzeit erhöht, wenn es mit verglichen wird eine `static``readonly` Feld.

 Da dem verwendeten Feld zugewiesene Wert zum Zeitpunkt der Kompilierung zu berechnendes ist, ändern Sie die Deklaration zu einem `const` Feld, sodass der Wert zur Kompilierzeit statt zur Laufzeit berechnet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen die `static` und `readonly` Modifizierer mit den `const` Modifizierer.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Gefahrlos unterdrücken einer Warnung dieser Regel oder die Regel deaktivieren, wenn die Leistung nicht relevant ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `UseReadOnly`, die gegen die Regel und einen Typ, `UseConstant`, die die Regel erfüllt.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
