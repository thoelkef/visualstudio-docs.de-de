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
ms.openlocfilehash: e85ac61e404ac9bc1afb9459716c2395233c5080
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607404"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Übermäßige Klassenkopplungen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategorie|Microsoft. Wartbarkeit|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ oder eine Methode ist mit vielen anderen Typen verknüpft.

## <a name="rule-description"></a>Regelbeschreibung
 Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.

 Typen und Methoden mit einem hohen Grad an Klassen Kopplung können schwer zu verwalten sein. Es empfiehlt sich, Typen und Methoden zu nutzen, die eine geringe Kopplung und einen hohen Zusammenhalt aufweisen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, versuchen Sie, den Typ oder die Methode umzugestalten, um die Anzahl der Typen, mit denen Sie gekoppelt ist, zu reduzieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Schließen Sie diese Warnung aus, wenn der Typ oder die Methode trotz der großen Anzahl von Abhängigkeiten von anderen Typen weiterhin als wart Bar eingestuft wird.

## <a name="see-also"></a>Siehe auch
 [Wart barkeits Warnungen](../code-quality/maintainability-warnings.md) , die die [Komplexität und Verwaltbarkeit von verwaltetem Code Messen](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
