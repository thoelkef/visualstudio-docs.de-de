---
title: 'CA1012: abstrakte Typen dürfen keine Konstruktoren aufweisen. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f3f53e8b5eab78e79387c24643500888db27b764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663228"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Abstrakte Typen dürfen keine Konstruktoren aufweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Abstracttypesschuldnothaveconstructors|
|CheckId|CA1012|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ ist abstrakt und verfügt über einen öffentlichen Konstruktor.

## <a name="rule-description"></a>Regelbeschreibung
 Konstruktoren von abstrakten Datentypen können nur von abgeleiteten Typen aufgerufen werden. Da öffentliche Konstruktoren Instanzen eines Typs erstellen und Sie keine Instanzen eines abstrakten Datentyps erstellen können, ist ein abstrakter Datentyp mit einem öffentlichen Konstruktor fehlerhaft konzipiert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie entweder den Konstruktor geschützt, oder deklarieren Sie den Typ nicht als abstrakt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Der abstrakte Typ verfügt über einen öffentlichen Konstruktor.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält einen abstrakten Typ, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/cs/FxCop.Design.AbstractTypeBad.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeBad/vb/FxCop.Design.AbstractTypeBad.vb#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der vorherige Verstoß behoben, indem der Zugriff auf den-Konstruktor von `public` in `protected` geändert wird.

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/cs/FxCop.Design.AbstractTypeGood.cs#1)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AbstractTypeGood/vb/FxCop.Design.AbstractTypeGood.vb#1)]
