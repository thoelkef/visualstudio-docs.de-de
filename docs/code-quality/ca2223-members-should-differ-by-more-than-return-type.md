---
title: 'CA2223: Member sollten sich durch mehr als den Rückgabetyp unterscheiden.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c09239fbb904edac6481cee372b9e96e0183b62a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890779"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: Member sollten sich durch mehr als den Rückgabetyp unterscheiden.

|||
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Zwei öffentliche oder geschützte Member verfügen Signaturen, die mit Ausnahme der Rückgabetyp identisch sind.

## <a name="rule-description"></a>Regelbeschreibung
 Die common Language Runtime lässt die Verwendung von Rückgabetypen zwischen anderweitig identischen Membern unterschieden werden kann, wird dieses Feature befindet sich nicht in der Common Language Specification, noch ist es eine allgemeine Funktion von .NET-Programmiersprachen. Wenn Member nur durch den Rückgabetyp unterscheiden zu können, können Entwickler und nicht ordnungsgemäß zwischen ihnen unterscheiden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf der Elemente, damit sie eindeutig nur auf ihren Namen und die Parametertypen basieren sind, oder Sie die Elemente nicht machen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt in Microsoft intermediate Language (MSIL), einen Typ, der gegen diese Regel verstößt. Beachten Sie, dass diese Regel kann nicht verletzt werden, mithilfe von c# oder Visual Basic.

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