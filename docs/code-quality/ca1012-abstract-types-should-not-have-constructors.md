---
title: 'CA1012: Abstrakte Typen dürfen keine Konstruktoren aufweisen.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ef4bff83b1921b3cf15b25aaf225645379478f38
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236351"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: Abstrakte Typen dürfen keine Konstruktoren aufweisen.

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ ist abstrakt und verfügt über einen Konstruktor.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Konstruktoren von abstrakten Datentypen können nur von abgeleiteten Typen aufgerufen werden. Da öffentliche Konstruktoren Instanzen eines Typs erstellen und keine Instanzen eines abstrakten Typs erstellt werden können, ist ein abstrakter Typ mit einem öffentlichen Konstruktor falsch entworfen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, stellen Sie entweder den Konstruktor geschützt, oder deklarieren Sie den Typ nicht als abstrakt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel. Der abstrakte Typ verfügt über einen öffentlichen Konstruktor.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1012.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Der folgende Code Ausschnitt enthält einen abstrakten Typ, der gegen diese Regel verstößt.

[!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
[!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

Der folgende Code Ausschnitt korrigiert die vorherige Verletzung durch Ändern des Zugriffs auf den Konstruktor von `public` in. `protected`

[!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
[!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]