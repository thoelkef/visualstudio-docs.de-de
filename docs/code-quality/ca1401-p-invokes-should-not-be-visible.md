---
title: 'CA1401: P ruft dürfen nicht sichtbar sein'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e085d096a18f7d7bf76c9ab738057ab3a1187ee2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes dürfen nicht sichtbar sein
|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über die <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut (auch durch implementiert die `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="rule-description"></a>Regelbeschreibung
 Mit markierte Methoden der <xref:System.Runtime.InteropServices.DllImportAttribute> Attribut (oder mit definierten Methoden den `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Platform Invocation Services den Zugriff auf nicht verwalteten Code verwenden. Solche Methoden sollten nicht verfügbar gemacht werden. Durch diese Methoden Speicherung der privaten oder internen, stellen Sie sicher, dass Ihre Bibliothek verwendet werden kann, um Sicherheit zu gefährden, dem Aufrufer Zugriff auf nicht verwaltete APIs, die sie andernfalls nicht aufrufen können.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene der Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel deklariert eine Methode, die mit dieser Regel verletzt.

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]