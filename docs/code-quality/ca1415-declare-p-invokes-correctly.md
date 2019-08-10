---
title: 'CA1415: P/Invokes korrekt deklarieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cc12d5d0a62f8d2530f13fcf860aba4e118ca4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921856"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invokes korrekt deklarieren.

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend: Wenn der P/Aufruf, der den Parameter deklariert, außerhalb der Assembly nicht sichtbar ist. Unterbrechung: Wenn der P/Aufruf, der den Parameter deklariert, außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
Eine Platt Form Aufruf Methode wurde falsch deklariert.

## <a name="rule-description"></a>Regelbeschreibung
Eine Platt Form Aufruf Methode greift auf nicht verwalteten Code zu und wird mithilfe `Declare` des- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Schlüssel Worts <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>in oder definiert. Derzeit sucht diese Regel nach Platt Form Aufruf-Methoden Deklarationen, die auf Win32-Funktionen abzielen, die einen Zeiger auf einen übergebenen Struktur Parameter aufweisen, und der entsprechende verwaltete Parameter <xref:System.Threading.NativeOverlapped?displayProperty=fullName> ist kein Zeiger auf eine-Struktur.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, deklarieren Sie die Platt Form Aufruf Methode ordnungsgemäß.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt Platt Form Aufruf Methoden, die gegen die Regel verstoßen und die Regel erfüllen.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Siehe auch
[Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)