---
title: 'CA1064: Ausnahmen sollten öffentlich sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b60127eee3ea333e324c656961eaf383a6ef409f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898560"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Ausnahmen sollten öffentlich sein
|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine nicht öffentliche Ausnahme wird direkt von abgeleitet <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>.

## <a name="rule-description"></a>Regelbeschreibung
 Eine interne Ausnahme ist nur innerhalb ihres eigenen internen Bereichs sichtbar. Nachdem die Ausnahme den internen Bereich verlassen hat, kann nur die Basisausnahme zum Abfangen der Ausnahme verwendet werden. Wenn die interne Ausnahme erbt <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>, der externe Code haben nicht genügend Informationen zur Behandlung der Ausnahme.

 Aber der Code eine öffentliche Ausnahme enthalten ist, die später als Basis für eine interne Ausnahme verwendet wird, wird davon ausgegangen, dass der Code weiter können die Basisausnahme intelligente werden. Die öffentliche Ausnahme mehr Informationen als von bereitgestellt werden müssen <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wandeln Sie die Ausnahme, oder leiten Sie die interne Ausnahme von einer öffentlichen Ausnahme außer <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Meldung dieser Regel, wenn Sie in allen Fällen sicher sind, dass die private Ausnahme innerhalb ihres eigenen internen Bereichs abgefangen wird.

## <a name="example"></a>Beispiel
 Diese Regel wird bei der ersten Beispielmethode ausgelöst (FirstCustomException), da die Ausnahmeklasse direkt von Exception abgeleitet und interne. Die Regel wird nicht auf die SecondCustomException-Klasse ausgelöst, denn obwohl die Klasse auch von der Exception abgeleitet ist, die Klasse als öffentlich deklariert ist. Die dritte Klasse auch löst nicht die Regel, da es nicht direkt abgeleitet ist <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, oder <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
