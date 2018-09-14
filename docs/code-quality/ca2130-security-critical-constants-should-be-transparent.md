---
title: 'CA2130: Sicherheitskritische Konstanten sollten transparent sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 212bd1bc9f1f5b66fa8ddb485c5ec287ff39c754
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551349"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Sicherheitskritische Konstanten sollten transparent sein
|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein konstantes Feld oder ein Enumerationsmember ist mit markiert die <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Regelbeschreibung
 Transparenzerzwingung wird nicht für konstante Werte erzwungen, da Compiler konstante Werte inline verwenden, damit zur Laufzeit keine Suche erforderlich ist. Konstante Felder sollten sicherheitstransparent sein, damit Codebearbeiter nicht davon ausgehen, dass dieser transparente Code nicht auf die Konstante zugreifen kann.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das SecurityCritical-Attribut aus dem Feld oder einen Wert ein.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In den folgenden Beispielen wird der Enum-Wert `EnumWithCriticalValues.CriticalEnumValue` und die Konstante `CriticalConstant` diese Warnung auslösen. Um die Probleme zu beheben, entfernen Sie die [`SecurityCritical`]-Attribut diese transparent zu gestalten.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]