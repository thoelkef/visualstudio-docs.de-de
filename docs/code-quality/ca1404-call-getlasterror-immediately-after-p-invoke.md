---
title: 'CA1404: GetLastError unmittelbar nach P-Invoke aufrufen'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6529adafa7384bf8b51444dd2cc81b9952b6b57c
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349019"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: GetLastError unmittelbar nach P/Invoke aufrufen

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategorie|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>-Methode oder die entsprechende Win32 `GetLastError`-Funktion wird aufgerufen, und der Aufruf, der unmittelbar vor erfolgt, erfolgt nicht in einer Platt Form Aufruf Methode.

## <a name="rule-description"></a>Regelbeschreibung
Eine Platt Form Aufruf Methode greift auf nicht verwalteten Code zu und wird mit dem `Declare`-Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>-Attribut definiert. Im Allgemeinen wird bei einem Fehler von nicht verwalteten Funktionen die Win32-Funktion "`SetLastError`" aufgerufen, um einen Fehlercode festzulegen, der dem Fehler zugeordnet ist. Der Aufrufer der fehlgeschlagenen Funktion Ruft die Win32-Funktion "`GetLastError`" auf, um den Fehlercode abzurufen und die Ursache des Fehlers zu ermitteln. Der Fehlercode wird Thread bezogen verwaltet und durch den nächsten `SetLastError`-Aufrufe überschrieben. Nach einem Aufruf einer fehlgeschlagenen Platt Form Aufruf Methode kann verwalteter Code den Fehlercode abrufen, indem er die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>-Methode aufruft. Da der Fehlercode von internen Aufrufen von anderen Methoden der verwalteten Klassenbibliothek überschrieben werden kann, sollte die `GetLastError`-oder <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>-Methode unmittelbar nach dem Aufruf der Platt Form Aufruf Methode aufgerufen werden.

Die Regel ignoriert Aufrufe der folgenden verwalteten Member, wenn Sie zwischen dem Aufruf der Platt Form Aufruf Methode und dem Aufruf von <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> auftreten. Diese Member ändern den Fehlercode nicht und sind hilfreich, um die erfolgreiche Ausführung einiger Platt Form Aufrufe von Platt Form aufrufen zu ermitteln.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie den Aufruf in <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>, sodass er unmittelbar auf den Aufruf der Platt Form Aufruf Methode folgt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Code zwischen dem Platt Form Aufruf Methodenaufruf und dem <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>-Methodenaufruf nicht explizit oder implizit bewirken kann, dass der Fehlercode geändert wird.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt, und eine Methode, die die Regel erfüllt.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1060: P-Invokes in NativeMethods-Klasse verschieben](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400: Für P-Invoke müssen Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401: P-Invokes dürfen nicht sichtbar sein](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101: Marshalling für P-Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

[CA2205: Verwaltete Entsprechungen der Win32-API verwenden](../code-quality/ca2205.md)