---
title: 'CA1404: GetLastError unmittelbar nach P/Invoke aufrufen.'
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
ms.openlocfilehash: ab789e578dd8603f604cdb00aa5d236250d13670
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235053"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: GetLastError unmittelbar nach P/Invoke aufrufen.

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Es wird ein Aufruf an die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> -Methode oder die entsprechende `GetLastError` Win32-Funktion durchgeführt, und der Aufruf, der unmittelbar vor erfolgt, erfolgt nicht in einer Platt Form Aufruf Methode.

## <a name="rule-description"></a>Regelbeschreibung
Eine Platt Form Aufruf Methode greift auf nicht verwalteten Code zu und wird mit `Declare` dem- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Schlüsselwort <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> in oder dem-Attribut definiert. Im Allgemeinen wird bei einem Fehler von nicht verwalteten Funktionen die `SetLastError` Win32-Funktion aufgerufen, um einen Fehlercode festzulegen, der dem Fehler zugeordnet ist. Der Aufrufer der fehlgeschlagenen Funktion `GetLastError` Ruft die Win32-Funktion auf, um den Fehlercode abzurufen und die Ursache des Fehlers zu ermitteln. Der Fehlercode wird Thread bezogen verwaltet und durch den nächsten `SetLastError`-Befehl überschrieben. Nach einem Aufruf einer fehlgeschlagenen Platt Form Aufruf Methode kann verwalteter Code den Fehlercode abrufen, <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> indem er die-Methode aufruft. Da der Fehlercode von internen Aufrufen von anderen Methoden der verwalteten Klassenbibliothek überschrieben werden kann `GetLastError` , <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> sollte die-Methode oder die-Methode unmittelbar nach dem Aufruf der Platt Form Aufruf Methode aufgerufen werden.

Die Regel ignoriert Aufrufe der folgenden verwalteten Member, wenn Sie zwischen dem Aufruf der Platt Form Aufruf Methode und dem Aufruf <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>von auftreten. Diese Member ändern den Fehlercode nicht und sind hilfreich, um die erfolgreiche Ausführung einiger Platt Form Aufrufe von Platt Form aufrufen zu ermitteln.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie den <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Aufruf von so, dass er unmittelbar auf den Aufruf der Platt Form Aufruf Methode folgt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Code zwischen dem Platt Form Aufruf <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> -Methodenaufruf und dem Methodenaufruf nicht explizit oder implizit bewirken kann, dass der Fehlercode geändert wird.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt, und eine Methode, die die Regel erfüllt.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1060: Verschieben von P/aufrufen in die NativeMethods-Klasse](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400: P/aufrufende Einstiegspunkte müssen vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401: P/Aufrufe dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101: Marshalling für P/Aufruf-Zeichen folgen Argumente angeben](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

[CA2205: Verwaltete Entsprechungen der Win32-API verwenden](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)