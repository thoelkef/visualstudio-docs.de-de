---
title: 'CA1407: statische Member in für COM sichtbaren Typen vermeiden | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 436a8614c18c296c072d91116143306d898f0436
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538852"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Statische Member in für COM sichtbaren Typen vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ, der speziell für Component Object Model (com) als sichtbar gekennzeichnet ist, enthält eine- `public``static` Methode.

## <a name="rule-description"></a>Beschreibung der Regel
 COM unterstützt keine `static` Methoden.

 Diese Regel ignoriert Eigenschafts-und Ereignisaccessoren, Operator Überladungsmethoden oder Methoden, die entweder mit dem- <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Attribut oder dem-Attribut markiert sind <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> .

 Standardmäßig sind die folgenden Elemente für com sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member der öffentlichen Werttypen.

 Damit diese Regel auftritt, muss auf Assemblyebene der Wert <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt werden, `false` und die-Klasse <xref:System.Runtime.InteropServices.ComVisibleAttribute> muss auf festgelegt werden `true` , wie im folgenden Code gezeigt.

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
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf so, dass eine Instanzmethode verwendet wird, die dieselbe Funktionalität wie die-Methode bereitstellt `static` .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn ein com-Client keinen Zugriff auf die Funktionen benötigt, die von der-Methode bereitgestellt werden `static` .

## <a name="example-violation"></a>Beispiel Verstoß

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt eine `static` Methode, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Kommentare
 In diesem Beispiel kann die **Book. FromPages** -Methode nicht von com aufgerufen werden.

## <a name="example-fix"></a>Beispiel Korrektur

### <a name="description"></a>BESCHREIBUNG
 Um die Verletzung im vorherigen Beispiel zu beheben, können Sie die Methode in eine Instanzmethode ändern, aber dies ist in dieser Instanz nicht sinnvoll. Eine bessere Lösung besteht darin, explizit `ComVisible(false)` auf die-Methode anzuwenden, um anderen Entwicklern zu helfen, dass die Methode von com nicht angezeigt werden kann.

 Das folgende Beispiel gilt <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> für die-Methode.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1017: Assemblys mit ComVisibleAttribute markieren.](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden.](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden.](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Weitere Informationen
 [Interoperabilität mit nicht verwaltetem Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
