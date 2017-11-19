---
title: "CA1407: Statische Member in für COM sichtbaren Typen vermeiden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 43240b8969026a8bbec18528230d3ca97bcb2236
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: Statische Member in für COM sichtbaren Typen vermeiden
|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|CheckId|CA1407|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Typ, die speziell für Component Object Model (COM) als sichtbar markiert ist, enthält eine `public``static` Methode.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 COM unterstützt keine `static` Methoden.  
  
 Mit dieser Regel werden ignoriert, Eigenschaft und Ereignisaccessoren, Überladen von Methoden oder Methoden, die markiert sind, indem Sie entweder die <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> Attribut oder die <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> Attribut.  
  
 Standardmäßig sind die folgenden für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member von öffentlichen Werttypen.  
  
 Für diese Regel ausgeführt werden, ein auf Assemblyebene <xref:System.Runtime.InteropServices.ComVisibleAttribute> muss festgelegt werden, um `false` "und"-Klasse - <xref:System.Runtime.InteropServices.ComVisibleAttribute> muss festgelegt werden, um `true`, wie der folgende Code zeigt.  
  
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
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf an eine Instanzmethode zu verwenden, die bietet die gleiche Funktionalität wie die `static` Methode.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Ist eine Warnung dieser Regel zu unterdrücken, wenn ein COM-Client kein Zugriff auf die Funktionalität erforderlich ist, die von bereitgestellte sicher der `static` Methode.  
  
## <a name="example-violation"></a>Beispiel für einen Verstoß  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt eine `static` Methode, die mit dieser Regel verletzt.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### <a name="comments"></a>Kommentare  
 In diesem Beispiel wird die **Book.FromPages** Methode kann nicht aus COM aufgerufen werden  
  
## <a name="example-fix"></a>Korrektur für Beispiel  
  
### <a name="description"></a>Beschreibung  
 Zum Beheben des Verstoßes im vorherigen Beispiel können Sie die Methode ändern, an eine Instanzmethode, aber, die keinen Sinn in dieser Instanz. Eine bessere Lösung besteht darin, explizites übernehmen von `ComVisible(false)` an die Methode zum Deaktivieren an andere Entwickler zu vereinfachen, dass die Methode nicht aus COM sichtbar sein  
  
 Das folgende Beispiel wendet <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> an die Methode.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperabilität mit nicht verwaltetem Code](/dotnet/framework/interop/index)