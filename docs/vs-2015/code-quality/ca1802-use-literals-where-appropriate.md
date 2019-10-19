---
title: 'CA1802: Literale nach Bedarf verwenden | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bbcf83772a7a4031cf2e27abe7e8f4c08e21c11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671514"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Nach Möglichkeit Literale verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Feld wird als `static` deklariert und `readonly` (`Shared` und `ReadOnly` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) und mit einem Wert initialisiert, der zur Kompilierzeit berechnet werden kann.

## <a name="rule-description"></a>Regelbeschreibung
 Der Wert eines `static``readonly` Felds wird zur Laufzeit berechnet, wenn der statische Konstruktor für den deklarierenden Typ aufgerufen wird. Wenn das `static``readonly`-Feld initialisiert wird, wenn es deklariert wird und ein statischer Konstruktor nicht explizit deklariert wird, gibt der Compiler einen statischen Konstruktor aus, um das Feld zu initialisieren.

 Der Wert eines `const` Felds wird zur Kompilierzeit berechnet und in den Metadaten gespeichert, wodurch die Laufzeitleistung beim Vergleich mit einem `static``readonly` Feld erhöht wird.

 Da der Wert, der dem Zielfeld zugewiesen ist, zur Kompilierzeit komprimiert werden kann, ändern Sie die Deklaration in ein `const` Feld, sodass der Wert zur Kompilierzeit anstelle der Laufzeit berechnet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die `static`-und `readonly`-Modifizierer durch den `const`-Modifizierer.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken oder die Regel zu deaktivieren, wenn die Leistung nicht relevant ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `UseReadOnly`, der gegen die Regel verstößt, und einen Typ, `UseConstant`, der die Regel erfüllt.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
