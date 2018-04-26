---
title: ': Ca1414 boolesche P / Invoke-Argumente mit MarshalAs markieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19536941f0b4b3d96255cb9eb323bea5d4e899bf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren
|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Plattformaufrufmethode Deklaration enthält eine <xref:System.Boolean?displayProperty=fullName> Parameter-oder Rückgabewert jedoch <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> -Attribut nicht auf den Wert Parameters oder des Rückgabewerts angewendet wird.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code und wird definiert, mit der `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Gibt an, die Marshalling-Verhalten, das zum Konvertieren von Datentypen zwischen verwaltetem und nicht verwaltetem Code verwendet wird. Viele einfache Datentypen, wie z. B. <xref:System.Byte?displayProperty=fullName> und <xref:System.Int32?displayProperty=fullName>, verfügen über eine einzige Darstellung in nicht verwaltetem Code und erfordern keine Angabe der Marshalling-Verhalten; die common Language Runtime stellt automatisch das richtige Verhalten.

 Die <xref:System.Boolean> Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. Wenn die <xref:System.Runtime.InteropServices.MarshalAsAttribute> nicht angegeben wird, das standardmäßige Marshallingverhalten für die <xref:System.Boolean> Datentyp <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Dies ist eine 32-Bit-Ganzzahl, die in allen Fällen nicht geeignet ist. Boolean-Darstellung, die nicht verwaltete Methode benötigt bestimmt und an die entsprechende abgeglichen werden soll <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool ist der Win32-BOOL-Typ, der immer 4 Bytes. UnmanagedType.U1 kommt für C++ `bool` oder andere 1-Byte-Typen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden <xref:System.Runtime.InteropServices.MarshalAsAttribute> auf die <xref:System.Boolean> Parameter-oder Rückgabewert. Legen Sie den Wert des Attributs an die entsprechende <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Auch wenn die standardmäßiges Marshallingverhalten geeignet ist, bleibt der Code leichter, wenn das Verhalten explizit angegeben wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Plattformaufrufmethoden, die mit dem entsprechenden markiert sind <xref:System.Runtime.InteropServices.MarshalAsAttribute> Attribute.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1901: Deklarationen von P/Invoke müssen portabel sein.](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [: Ca2101 Marshalling für P/Invoke-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Interoperation mit nicht verwaltetem Code](/dotnet/framework/interop/index)