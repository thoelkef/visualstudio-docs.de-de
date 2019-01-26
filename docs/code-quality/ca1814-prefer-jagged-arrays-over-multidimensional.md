---
title: 'CA1814: Jagged Arrays mehrdimensionalen Arrays vorziehen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4ae26b9c9fdce13566a1110d9dda9554556efb3c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54926695"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Jagged Arrays mehrdimensionalen Arrays vorziehen.

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Element wird als ein mehrdimensionales Array deklariert.

## <a name="rule-description"></a>Regelbeschreibung
 Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind. Die Arrays, die die Elemente bilden, können unterschiedliche Größen haben, was bei einigen Gruppen von Daten dazu führt, dass weniger Speicherplatz vergeudet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das mehrdimensionale Array in ein verzweigtes Array ein.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel, wenn es sich bei das mehrdimensionale Array Speicherplatz nicht verschwendet wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Deklarationen für verzweigte und mehrdimensionale Arrays.

 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]