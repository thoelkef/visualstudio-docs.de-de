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
ms.openlocfilehash: 999a4a15dd83db66365bc9ee3701fd3130cedeb1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
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
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das SecurityCritical-Attribut aus dem Feld oder Wert ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In den folgenden Beispielen wird der Enum-Wert `EnumWithCriticalValues.CriticalEnumValue` und die Konstante `CriticalConstant` diese Warnung ausgelöst. Um die Probleme zu beheben, entfernen Sie das [`SecurityCritical`] Attribut, um sie transparent zu gestalten.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]