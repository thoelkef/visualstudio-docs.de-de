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
ms.openlocfilehash: 5114f6015d055c03d54d49deee1197b7e3d9c9da
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867676"
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

Diese Regel nur sucht standardmäßig an extern sichtbare Typen, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Konstruktoren von abstrakten Datentypen können nur von abgeleiteten Typen aufgerufen werden. Da öffentliche Konstruktoren Instanzen eines Typs erstellen, und Sie keine Instanzen eines abstrakten Datentyps erstellen, ist ein abstrakter Typ, der einem öffentlichen Konstruktor fehlerhaft konzipiert.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, dass der geschützte Konstruktor oder nicht den Typ als abstrakt deklariert.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel. Der abstrakte Typ verfügt über einen öffentlichen Konstruktor.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1012.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Der folgende Codeausschnitt enthält einen abstrakten Typ, der gegen diese Regel verstößt.

[!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
[!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

Im folgenden Codeausschnitt wird der vorherige Verstoß korrigiert, ändern Sie den Zugriff auf den Konstruktor von `public` zu `protected`.

[!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
[!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]