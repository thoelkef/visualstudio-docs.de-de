---
title: 'CA1064: Ausnahmen sollten öffentlich sein.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b17ccfe66875588ac19c587ff6fcbd889d1e6a44
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922315"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Ausnahmen sollten öffentlich sein.

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
Eine nicht öffentliche Ausnahme wird direkt von <xref:System.Exception>, <xref:System.SystemException>oder <xref:System.ApplicationException>abgeleitet.

## <a name="rule-description"></a>Regelbeschreibung
Eine interne Ausnahme ist nur innerhalb Ihres eigenen internen Bereichs sichtbar. Nachdem die Ausnahme den internen Bereich verlassen hat, kann nur die Basisausnahme zum Abfangen der Ausnahme verwendet werden. Wenn die interne Ausnahme von geerbt wird <xref:System.Exception>, <xref:System.SystemException>, oder <xref:System.ApplicationException>, der externe Code müssen nicht über genügend Informationen zur Vorgehensweise mit der Ausnahme.

Wenn der Code jedoch eine öffentliche Ausnahme aufweist, die später als Basis für eine interne Ausnahme verwendet wird, kann davon ausgegangen werden, dass der Code weiter unten mit der Basis Ausnahme intelligent vorgehen kann. Die öffentliche Ausnahme enthält mehr Informationen, als von <xref:System.Exception>, <xref:System.SystemException>oder <xref:System.ApplicationException>bereitgestellt werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Legen Sie die Ausnahme als öffentlich fest, oder leiten Sie die interne Ausnahme von einer öffentlichen <xref:System.Exception>Ausnahme <xref:System.SystemException>ab, <xref:System.ApplicationException>die nicht, oder ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie eine Nachricht aus dieser Regel, wenn Sie sicher sind, dass die private Ausnahme innerhalb Ihres eigenen internen Bereichs abgefangen wird.

## <a name="example"></a>Beispiel
Diese Regel wird für die erste Beispiel Methode, firstcustomexception, ausgelöst, da die Exception-Klasse direkt von der Ausnahme abgeleitet und intern ist. Die Regel wird nicht in der secondcustomexception-Klasse ausgelöst, da die Klasse auch direkt von der Ausnahme abgeleitet ist, wird die Klasse als öffentlich deklariert. Die dritte Klasse führt die Regel auch nicht aus, da Sie nicht direkt von <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>oder <xref:System.ApplicationException?displayProperty=fullName>abgeleitet wird.

[!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
