---
title: 'CA2130: Sicherheitskritische Konstanten sollten transparent sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a33b650570981f5496813f575b1ae2413a960026
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920777"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Sicherheitskritische Konstanten sollten transparent sein.

|||
|-|-|
|TypeName|Constantsschuldbetransparent|
|CheckId|CA2130|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein konstantes Feld oder ein Enumerationsmember ist mit <xref:System.Security.SecurityCriticalAttribute>dem gekennzeichnet.

## <a name="rule-description"></a>Regelbeschreibung
Transparenzerzwingung wird nicht für konstante Werte erzwungen, da Compiler konstante Werte inline verwenden, damit zur Laufzeit keine Suche erforderlich ist. Konstante Felder sollten sicherheitstransparent sein, damit Codebearbeiter nicht davon ausgehen, dass dieser transparente Code nicht auf die Konstante zugreifen kann.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das SecurityCritical-Attribut aus dem Feld oder dem Wert.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
In den folgenden Beispielen wird diese Warnung durch den `EnumWithCriticalValues.CriticalEnumValue` Enumerationswert und die Konstante `CriticalConstant` ausgegeben. Um die Probleme zu beheben, entfernen Sie`SecurityCritical`das []-Attribut, um die Sicherheit zu gewährleisten.

[!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]