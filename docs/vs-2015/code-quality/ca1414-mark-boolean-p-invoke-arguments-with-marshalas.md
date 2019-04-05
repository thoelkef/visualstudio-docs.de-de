---
title: 'CA1414: Boolesche P / Invoke-Argumente mit MarshalAs markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e444519c5a6d6d1547b782006d063e90d4a3b976
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960847"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Plattformaufrufmethode Deklaration enthält eine <xref:System.Boolean?displayProperty=fullName> Parameter oder Rückgabewert jedoch <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> -Attribut nicht auf den Wert für Parameter oder Rückgabewert angewendet wird.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code und ist definiert, mit der `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] oder <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Gibt an, das Marshalling-Verhalten, das zum Konvertieren von Datentypen zwischen verwaltetem und nicht verwaltetem Code verwendet wird. Viele einfache Datentypen, z. B. <xref:System.Byte?displayProperty=fullName> und <xref:System.Int32?displayProperty=fullName>, verfügen über eine einzelne Darstellung in nicht verwaltetem Code und erfordern keine Spezifikation von deren Marshalling-Verhalten; die common Language Runtime stellt automatisch das richtige Verhalten.

 Die <xref:System.Boolean> Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code. Wenn die <xref:System.Runtime.InteropServices.MarshalAsAttribute> nicht angegeben ist, das standardmäßige Marshallingverhalten für die <xref:System.Boolean> Datentyp <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Dies ist eine 32-Bit-Ganzzahl, die nicht in allen Fällen geeignet ist. Boolesche Darstellung, die erforderlich ist, die nicht verwaltete Methode sollten ermittelt und abgeglichen, die an die entsprechende <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool ist der Win32-BOOL-Typ, der immer 4 Byte ist. UnmanagedType.U1 kommt für C++ `bool` oder andere 1-Byte-Typen. Weitere Informationen finden Sie unter [Standardmäßiges Marshalling für boolesche Typen](http://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden <xref:System.Runtime.InteropServices.MarshalAsAttribute> auf die <xref:System.Boolean> Parameter oder Rückgabewert. Legen Sie den Wert des Attributs an die entsprechende <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Auch wenn das standardmäßige Marshallingverhalten geeignet ist, wird der Code leichter verwaltet werden, wird das Verhalten explizit angegeben.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden, mit dem entsprechenden markiert sind, für Plattformaufruf <xref:System.Runtime.InteropServices.MarshalAsAttribute> Attribute.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1901: Deklarationen von P/Invoke müssen portabel sein](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Geben Sie die Marshalling für P/Invoke-Zeichenfolgenargumente](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Standardmäßiges Marshalling für boolesche Typen](http://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [Interoperation mit nicht verwaltetem Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
