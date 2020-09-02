---
title: 'CA1404: GetLastError unmittelbar nach P-aufrufen aufrufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 54ac9a4d56136d9e981ae038a0b219aa4cb4774e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544494"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: GetLastError unmittelbar nach P/Invoke aufrufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Es wird ein Aufruf an die- <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> Methode oder die entsprechende Win32 `GetLastError` -Funktion durchgeführt, und der Aufruf, der unmittelbar vor erfolgt, erfolgt nicht in einer Platt Form Aufruf Methode.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine Platt Form Aufruf Methode greift auf nicht verwalteten Code zu und wird mit dem- `Declare` Schlüsselwort in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] oder dem- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut definiert. Im Allgemeinen wird bei einem Fehler von nicht verwalteten Funktionen die Win32-Funktion aufgerufen, `SetLastError` um einen Fehlercode festzulegen, der dem Fehler zugeordnet ist. Der Aufrufer der fehlgeschlagenen Funktion Ruft die Win32 `GetLastError` -Funktion auf, um den Fehlercode abzurufen und die Ursache des Fehlers zu ermitteln. Der Fehlercode wird Thread bezogen verwaltet und durch den nächsten-Befehl überschrieben `SetLastError` . Nach einem Aufruf einer fehlgeschlagenen Platt Form Aufruf Methode kann verwalteter Code den Fehlercode abrufen, indem er die- <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Methode aufruft. Da der Fehlercode von internen Aufrufen von anderen Methoden der verwalteten Klassenbibliothek überschrieben werden kann, sollte die- `GetLastError` Methode oder die- <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Methode unmittelbar nach dem Aufruf der Platt Form Aufruf Methode aufgerufen werden.

 Die Regel ignoriert Aufrufe der folgenden verwalteten Member, wenn Sie zwischen dem Aufruf der Platt Form Aufruf Methode und dem Aufruf von auftreten <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> . Diese Member ändern den Fehlercode nicht und sind hilfreich, um die erfolgreiche Ausführung einiger Platt Form Aufrufe von Platt Form aufrufen zu ermitteln.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie den Aufruf von <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> so, dass er unmittelbar auf den Aufruf der Platt Form Aufruf Methode folgt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Code zwischen dem Platt Form Aufruf-Methodenaufruf und dem <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> Methodenaufruf nicht explizit oder implizit bewirken kann, dass der Fehlercode geändert wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt, und eine Methode, die die Regel erfüllt.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1060: P/Aufrufe in die NativeMethods-Klasse verschieben](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: P/aufrufende Einstiegspunkte müssen vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Aufrufe dürfen nicht sichtbar sein.](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Marshalling für P/Aufruf-Zeichen folgen Argumente angeben](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Verwaltete Entsprechungen der Win32 API verwenden.](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
