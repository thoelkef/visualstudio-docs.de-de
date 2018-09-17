---
title: 'CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e829ae7f3546556ad80d0dd4c1d5d5b80eae9a4f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547421"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typen müssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen
|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein transparenter Typ wird abgeleitet von einem Typ, die mit der <xref:System.Security.SecuritySafeCriticalAttribute> oder <xref:System.Security.SecurityCriticalAttribute>, oder ein Typ, der mit markiert ist die <xref:System.Security.SecuritySafeCriticalAttribute> Attribut stammt von einem Typ, die mit der <xref:System.Security.SecurityCriticalAttribute> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird ausgelöst, wenn ein abgeleiteter Typ über ein Sicherheitstransparenzattribut verfügt, das nicht so wichtig wie der Basistyp oder die implementierte Schnittstelle ist. Nur wichtige Typen können von wichtigen Basistypen abgeleitet werden oder kritische Schnittstellen implementieren, und nur kritische oder sicherheitskritische Typen können von sicherheitskritischen Basistypen abgeleitet werden oder sicherheitskritische Schnittstellen implementieren. Verstöße gegen diese Regel in Transparenz der Ebene 2 führen eine <xref:System.TypeLoadException> für den abgeleiteten Typ.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, markieren Sie die abgeleiteten oder implementierenden Typ mit einem Transparenzattribut, das mindestens genauso kritisch sein wie der Basistyp oder die Schnittstelle ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]