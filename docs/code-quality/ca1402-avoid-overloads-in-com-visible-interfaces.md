---
title: "CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9294e1aab07aa05bc10de507e0a5885a47ebcc40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Überladungen in für COM sichtbaren Schnittstellen vermeiden
|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Kategorie|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine Component Object Model (COM) sichtbare Schnittstelle deklariert überladene Methoden.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Wenn für COM-Clients überladene Methoden verfügbar gemacht werden, behält nur die erste Methodenüberladung ihren Namen. Nachfolgende Überladungen werden eindeutig umbenannt, indem auf den Namen angefügt wird, einen Unterstrich "_" und eine ganze Zahl, die Reihenfolge der Deklaration der Überladung entspricht. Betrachten Sie beispielsweise die folgenden Methoden aus.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Diese Methoden werden für COM-Clients wie folgt verfügbar gemacht.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Visual Basic 6-COM-Clients können keine Schnittstellenmethoden implementieren, mit einem Unterstrich im Namen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie die überladenen Methoden, damit die Namen eindeutig sind. Alternativ können Sie die Schnittstelle für COM sichtbar machen durch ändern den Zugriff auf `internal` (`Friend` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) oder durch Anwenden der <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> -Attributsatz zur `false`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Schnittstelle, die die Regel verletzt und eine Schnittstelle, die die Regel erfüllt.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperation mit nicht verwaltetem Code](/dotnet/framework/interop/index)   
 [Long-Datentyp](/dotnet/visual-basic/language-reference/data-types/long-data-type)