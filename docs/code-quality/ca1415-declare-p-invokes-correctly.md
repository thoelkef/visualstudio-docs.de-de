---
title: 'CA1415: P-aufgerufen für korrekt deklarieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a690baeb804d3722d442c30077cc07d260a8952
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: P/Invokes korrekt deklarieren
|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend – Wenn P/Invoke, die den Parameter deklariert, nicht außerhalb der Assembly sichtbar ist. Unterbrechend – Wenn P/Invoke, die den Parameter deklariert, die außerhalb der Assembly sichtbar sein können.|

## <a name="cause"></a>Ursache
 Ein Plattformaufruf-Methode wurde falsch deklariert.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code und wird definiert, mit der `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Derzeit ist diese Regel sucht nach für Plattformaufruf Methodendeklarationen von Win32-Funktionen, bei denen einen Zeiger auf einen OVERLAPPED-Strukturparameter haben und der zugehörige verwaltete Parameter ist kein Zeiger auf eine <xref:System.Threading.NativeOverlapped?displayProperty=fullName> Struktur.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, die Plattform korrekt deklarieren invoke-Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt Plattformaufrufmethoden, die die Regel verletzen, und die Regel eingehalten.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Siehe auch
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)