---
title: "CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ed47a2ccea76ce9cb6e2a1ef6dd73d53c961544c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Int64-Argumente für Visual Basic 6-Clients vermeiden
|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Typ, der speziell als für Component Object Model (COM) sichtbar markiert ist deklariert einen Member, nimmt ein <xref:System.Int64?displayProperty=fullName> Argument.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Visual Basic 6-COM-Clients können nicht auf 64-Bit-Ganzzahlen zugreifen.  
  
 Standardmäßig sind die folgenden für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member von öffentlichen Werttypen. Allerdings erfordert diese Regel um falsch positive Ergebnisse zu reduzieren, die COM-Sichtbarkeit des Typs explizit angegeben werden; die enthaltende Assembly muss mit dem gekennzeichnet werden die <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> festgelegt `false` und der Typ muss markiert sein, mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt `true`.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel für einen Parameter zu beheben, dessen Wert immer als 32-Bit-Ganzzahl ausgedrückt werden, ändern Sie den Parametertyp in <xref:System.Int32?displayProperty=fullName>. Wenn der Wert des Parameters größer als 32-Bit-Ganzzahl dargestellt werden kann, ändern Sie den Parametertyp in <xref:System.Decimal?displayProperty=fullName>. Beachten Sie, dass beide <xref:System.Single?displayProperty=fullName> und <xref:System.Double?displayProperty=fullName> verlieren die oberen Bereiche der Genauigkeit der <xref:System.Int64> -Datentyp. Wenn der Member nicht für COM sichtbar sein sollen, markieren Sie es mit der <xref:System.Runtime.InteropServices.ComVisibleAttribute> festgelegt `false`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn sicher ist, dass Visual Basic 6-COM-Clients nicht auf den Typ zugreifen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt.  
  
 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperation mit nicht verwaltetem Code](/dotnet/framework/interop/index)   
 [Long-Datentyp](/dotnet/visual-basic/language-reference/data-types/long-data-type)