---
title: 'CA1814: verzweigte Arrays über mehrdimensional bevorzugen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f0ac183321bd2a3070b1f1ddc54402b74c8fb823
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668414"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: Verzweigte Arrays mehrdimensionalen Arrays vorziehen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Member wird als mehrdimensionales Array deklariert.

## <a name="rule-description"></a>Regelbeschreibung
 Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind. Die Arrays, die die Elemente bilden, können unterschiedliche Größen haben, was bei einigen Gruppen von Daten dazu führt, dass weniger Speicherplatz vergeudet wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das mehrdimensionale Array in ein Jagged Array.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn das mehrdimensionale Array keinen Speicherplatz verschwendet.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt Deklarationen für verzweigte und mehrdimensionale Arrays.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
