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
ms.openlocfilehash: 1a06197278c61a25c4baad15888f818ed1e1f673
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797362"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren.

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Plattformaufrufmethode Deklaration enthält eine <xref:System.Boolean?displayProperty=fullName> Parameter oder Rückgabewert jedoch <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> -Attribut nicht auf den Wert für Parameter oder Rückgabewert angewendet wird.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code und ist definiert, mit der `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Gibt an, das Marshalling-Verhalten, das zum Konvertieren von Datentypen zwischen verwaltetem und nicht verwaltetem Code verwendet wird. Viele einfache Datentypen, z. B. <xref:System.Byte?displayProperty=fullName> und <xref:System.Int32?displayProperty=fullName>, verfügen über eine einzelne Darstellung in nicht verwaltetem Code und erfordern keine Spezifikation von deren Marshalling-Verhalten; die common Language Runtime stellt automatisch das richtige Verhalten.

 Die <xref:System.Boolean> Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. Wenn die <xref:System.Runtime.InteropServices.MarshalAsAttribute> nicht angegeben ist, das standardmäßige Marshallingverhalten für die <xref:System.Boolean> Datentyp <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Dies ist eine 32-Bit-Ganzzahl, die nicht in allen Fällen geeignet ist. Boolesche Darstellung, die erforderlich ist, die nicht verwaltete Methode sollten ermittelt und abgeglichen, die an die entsprechende <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool ist der Win32-BOOL-Typ, der immer 4 Byte ist. UnmanagedType.U1 kommt für C++ `bool` oder andere 1-Byte-Typen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden <xref:System.Runtime.InteropServices.MarshalAsAttribute> auf die <xref:System.Boolean> Parameter oder Rückgabewert. Legen Sie den Wert des Attributs an die entsprechende <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Auch wenn das standardmäßige Marshallingverhalten geeignet ist, wird der Code leichter verwaltet werden, wird das Verhalten explizit angegeben.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt Plattformaufrufmethoden, die mit dem entsprechenden markiert sind <xref:System.Runtime.InteropServices.MarshalAsAttribute> Attribute.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1901: Deklarationen von P/Invoke müssen portabel sein](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Geben Sie die Marshalling für P/Invoke-Zeichenfolgenargumente](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)