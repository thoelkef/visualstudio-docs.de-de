---
title: 'CA1407: Statische Member in für COM sichtbaren Typen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 93c56c17998bbe672ed5816fc950eec5cc56b1c3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705735"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Statische Member in für COM sichtbaren Typen vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Kategorie|Microsoft.Interoperability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ, die speziell auf Component Object Model (COM) als sichtbar markiert ist, enthält eine `public``static` Methode.

## <a name="rule-description"></a>Regelbeschreibung
 COM unterstützt keine `static` Methoden.

 Mit dieser Regel werden ignoriert, Eigenschaft und Ereignisaccessoren, Überladen von Methoden oder Methoden, die markiert sind, indem Sie entweder die <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Attribut oder das <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> Attribut.

 Standardmäßig sind die folgenden für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Member in öffentlichen Typen und alle Mitglieder der öffentliche Werttypen.

 Für diese Regel vorgenommen wird, eine auf Assemblyebene <xref:System.Runtime.InteropServices.ComVisibleAttribute> muss festgelegt werden, um `false` "und" der Klasse - <xref:System.Runtime.InteropServices.ComVisibleAttribute> muss festgelegt werden, um `true`, wie der folgende Code zeigt.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das Design, um eine Instanzmethode zu verwenden, die die gleiche Funktionalität wie stellt der `static` Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicherer, die mit dieser Regel eine Warnung zu unterdrücken, wenn ein COM-Client keinen Zugriff auf die Funktionen erfordert, die von bereitgestellte der `static` Methode.

## <a name="example-violation"></a>Beispiel für einen Verstoß

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine `static` -Methode, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Kommentare
 In diesem Beispiel die **Book.FromPages** Methode kann nicht aus COM aufgerufen werden

## <a name="example-fix"></a>Korrektur für Beispiel

### <a name="description"></a>Beschreibung
 Sie können die Methode in einer Instanzmethode ändern, um die Verletzung der im vorherigen Beispiel zu beheben, allerdings, die nicht sinnvoll in dieser Instanz. Eine bessere Lösung ist, um explizit übernehmen `ComVisible(false)` auf die Methode, um anderen Entwicklern zu erleichtern, dass die Methode aus COM nicht sichtbar ist

 Im folgenden Beispiel wird <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> an die Methode.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Vermeiden Sie nicht öffentliche Felder in für COM sichtbaren Werttypen](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Siehe auch
 [Interoperabilität mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
