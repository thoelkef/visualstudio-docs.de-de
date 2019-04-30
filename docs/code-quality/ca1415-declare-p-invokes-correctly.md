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
ms.openlocfilehash: da6448a414437a07b545a999b35031f82e9a8689
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546185"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invokes korrekt deklarieren.

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der P/Invoke, die den Parameter deklariert, kann nicht außerhalb der Assembly angezeigt werden. Unterbrechend – Wenn der P/Invoke, die den Parameter deklariert, die außerhalb der Assembly angezeigt werden können.|

## <a name="cause"></a>Ursache
 Eine Plattformaufrufmethode wurde falsch deklariert.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code und ist definiert, mit der `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Derzeit diese Regel sucht Plattformaufrufdeklarationen Methode, die Win32-Funktionen als Ziel, die einen Zeiger auf einen OVERLAPPED-Strukturparameter haben und es ist nicht des zugehörigen verwalteten Parameters ein Zeiger auf eine <xref:System.Threading.NativeOverlapped?displayProperty=fullName> Struktur.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, deklarieren Sie ordnungsgemäß die Plattform invoke-Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt Plattformaufrufmethoden, die die Regel verletzen, und die Regel zu erfüllen.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Siehe auch
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)