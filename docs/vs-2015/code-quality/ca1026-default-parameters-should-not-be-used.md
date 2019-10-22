---
title: 'CA1026: Standardparameter sollten nicht verwendet werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8fffbdc2cf9f4e09fe98c8e14b6692802ab3f275
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661941"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: Standardparameter sollten nicht verwendet werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ enthält eine extern sichtbare Methode, die einen Standardparameter verwendet.

## <a name="rule-description"></a>Regelbeschreibung
 Methoden, die Standardparameter verwenden, sind unter dem Common Language Specification (CLS) zulässig. Allerdings können Compiler die Werte, die diesen Parametern zugewiesen sind, durch die CLS ignorieren. Code, der für Compiler geschrieben wird, die Standardparameter Werte ignorieren, muss explizit Argumente für jeden Standardparameter bereitstellen. Um das gewünschte Verhalten für Programmiersprachen beizubehalten, sollten Methoden, die Standardparameter verwenden, durch Methoden Überladungen ersetzt werden, die die Standardparameter bereitstellen.

 Der Compiler ignoriert die Werte der Standardparameter für die verwaltete Erweiterung C++ für den Zugriff auf verwalteten Code. Der Visual Basic-Compiler unterstützt Methoden, die über Standardparameter verfügen, die das [optionale](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) Schlüsselwort verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie die-Methode, die Standardparameter verwendet, mit Methoden Überladungen, die die Standardparameter bereitstellen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die Standardparameter verwendet, und die überladenen Methoden, die eine äquivalente Funktionalität bereitstellen.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1025: Sich wiederholende Argumente durch ein Parameterarray ersetzen](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Siehe auch
 [Sprachunabhängigkeit und sprachunabhängige Komponenten](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
