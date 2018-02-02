---
title: "CA2223: Member sollten sich durch mehr als den Rückgabetyp unterscheiden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4c72475c76a85216499a389d12f090ef302fc143
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: Member sollten sich durch mehr als nur den Rückgabetyp unterscheiden
|||  
|-|-|  
|TypeName|MembersShouldDifferByMoreThanReturnType|  
|CheckId|CA2223|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Zwei öffentliche oder geschützte Member haben Signaturen, die mit Ausnahme der Rückgabetyp identisch sind.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die common Language Runtime lässt die Verwendung von Rückgabetypen zu zwischen anderweitig identischen Membern unterschieden werden kann, wird diese Funktion befindet sich nicht in der Common Language Specification, noch ist es keine gebräuchliche Funktion von .NET-Programmiersprachen. Wenn Member nur durch den Rückgabetyp unterscheiden, können Entwickler und Entwicklungsprogramme nicht ordnungsgemäß zwischen ihnen unterschieden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf der Elemente, sodass eindeutige schon auf Grundlage ihrer Namen und Parametertypen oder Sie nicht die Member verfügbar machen.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird in Microsoft intermediate Language (MSIL), einen Typ, der mit dieser Regel verletzt. Beachten Sie, dass diese Regel kann nicht verletzt werden, mithilfe von c# oder Visual Basic.  
  
```  
  
.namespace UsageLibrary  
{  
  .class public auto ansi beforefieldinit ReturnTypeTest  
         extends [mscorlib]System.Object  
  {  
    .method public hidebysig instance int32  
            AMethod(int32 x) cil managed  
    {  
      // Code size       6 (0x6)  
      .maxstack  1  
      .locals init (int32 V_0)  
      IL_0000:  ldc.i4.0  
      IL_0001:  stloc.0  
      IL_0002:  br.s       IL_0004  
  
      IL_0004:  ldloc.0  
      IL_0005:  ret  
    } // end of method ReturnTypeTest::AMethod  
  
    .method public hidebysig instance string  
            AMethod(int32 x) cil managed  
    {  
      // Code size       10 (0xa)  
      .maxstack  1  
      .locals init (string V_0)  
      IL_0000:  ldstr      "test"  
      IL_0005:  stloc.0  
      IL_0006:  br.s       IL_0008  
  
      IL_0008:  ldloc.0  
      IL_0009:  ret  
    } // end of method ReturnTypeTest::AMethod  
  
    .method public hidebysig specialname rtspecialname  
            instance void  .ctor() cil managed  
    {  
      // Code size       7 (0x7)  
      .maxstack  1  
      IL_0000:  ldarg.0  
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()  
      IL_0006:  ret  
    } // end of method ReturnTypeTest::.ctor  
  
  } // end of class ReturnTypeTest  
  
} // end of namespace UsageLibrary  
  
```