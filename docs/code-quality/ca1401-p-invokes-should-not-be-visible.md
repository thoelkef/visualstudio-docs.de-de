---
title: 'CA1401: P/Invokes dürfen nicht sichtbar sein.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a139dd44c470422554dd2d5ccb42ab61a9d84637
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021402"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes dürfen nicht sichtbar sein.

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ hat die <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut (auch durch implementiert die `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Regelbeschreibung
 Mit markierte Methoden der <xref:System.Runtime.InteropServices.DllImportAttribute> Attribut (oder mithilfe von definierten Methoden den `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Platform Invocation Services den Zugriff auf nicht verwalteten Code verwenden. Solche Methoden sollten nicht verfügbar gemacht werden. Halten diese Methoden, private oder interne, stellen Sie sicher, dass die Bibliothek verwendet werden kann, um Sicherheitsrichtlinien zu umgehen, dass der Aufrufer den Zugriff auf nicht verwalteten APIs, die sie andernfalls nicht aufrufen konnte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene der Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel deklariert eine Methode, die gegen diese Regel verstößt.

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]