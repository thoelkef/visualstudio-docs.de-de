---
title: 'CA1506: übermäßige Klassen Kopplung vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 07f19cb9d4aa2ed118898a1816092479cbd16565
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545703"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Übermäßige Klassenkopplungen vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategorie|Microsoft. Wartbarkeit|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ oder eine Methode ist mit vielen anderen Typen verknüpft.

## <a name="rule-description"></a>Beschreibung der Regel
 Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.

 Typen und Methoden mit einem hohen Grad an Klassen Kopplung können schwer zu verwalten sein. Es empfiehlt sich, Typen und Methoden zu nutzen, die eine geringe Kopplung und einen hohen Zusammenhalt aufweisen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, versuchen Sie, den Typ oder die Methode umzugestalten, um die Anzahl der Typen, mit denen Sie gekoppelt ist, zu reduzieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Schließen Sie diese Warnung aus, wenn der Typ oder die Methode trotz der großen Anzahl von Abhängigkeiten von anderen Typen weiterhin als wart Bar eingestuft wird.

## <a name="see-also"></a>Weitere Informationen
 [Wart barkeits Warnungen](../code-quality/maintainability-warnings.md) , die die [Komplexität und Verwaltbarkeit von verwaltetem Code Messen](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
