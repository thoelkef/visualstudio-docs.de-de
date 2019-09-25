---
title: 'CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 22e62a1e3209399be4b10a3ec28db4afdd6f0f20
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234670"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren.

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine Platt Form Aufruf-Methoden Deklaration enthält einen Parameter oder <xref:System.Boolean?displayProperty=fullName> einen <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> Rückgabewert, aber das Attribut wird nicht auf den Parameter oder den Rückgabewert angewendet.

## <a name="rule-description"></a>Regelbeschreibung
Eine Platt Form Aufruf Methode greift auf nicht verwalteten Code zu und wird mithilfe `Declare` des- [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Schlüssel Worts <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>in oder definiert. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Gibt das Marshallingverhalten an, das zum Konvertieren von Datentypen zwischen verwaltetem und nicht verwaltetem Code verwendet wird. Viele einfache Datentypen, wie z <xref:System.Byte?displayProperty=fullName> . <xref:System.Int32?displayProperty=fullName>b. und, haben eine einzelne Darstellung in nicht verwaltetem Code und erfordern keine Angabe Ihres marshallingverhaltens. der Common Language Runtime liefert automatisch das richtige Verhalten.

Der <xref:System.Boolean> -Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. Wenn nicht angegeben wird, ist <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>das standardmäßige Marshallingverhalten für <xref:System.Boolean> den Datentyp. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Dies ist eine 32-Bit-Ganzzahl, die in allen Fällen nicht geeignet ist. Die boolesche Darstellung, die von der nicht verwalteten Methode benötigt wird, sollte bestimmt und mit dem entsprechenden <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>übereinstimmen. UnmanagedType. bool ist der Win32-boolesche Typ, bei dem es sich immer um 4 Bytes handelt. UnmanagedType. U1 sollte für C++ `bool` oder andere 1-Byte-Typen verwendet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, <xref:System.Runtime.InteropServices.MarshalAsAttribute> wenden Sie <xref:System.Boolean> auf den Parameter oder den Rückgabewert an. Legen Sie den Wert des-Attributs auf <xref:System.Runtime.InteropServices.UnmanagedType>den entsprechenden Wert fest.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel. Auch wenn das standardmäßige Marshalling-Verhalten angemessen ist, kann der Code leichter verwaltet werden, wenn das Verhalten explizit angegeben wird.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt Platt Form Aufruf Methoden, die mit den entsprechenden <xref:System.Runtime.InteropServices.MarshalAsAttribute> Attributen gekennzeichnet sind.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1901: P/Aufruf Deklarationen sollten portabel sein.](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101: Marshalling für P/Aufruf-Zeichen folgen Argumente angeben](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)