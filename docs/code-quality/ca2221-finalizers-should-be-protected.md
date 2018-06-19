---
title: 'CA2221: Finalizer sollten geschützt sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2221
- FinalizersShouldBeProtected
helpviewer_keywords:
- FinalizersShouldBeProtected
- CA2221
ms.assetid: bda03aee-4cce-45d3-907d-17f4ee030acc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25d67c99a9c2b30461170b7e8b5090e0c08241ee
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917868"
---
# <a name="ca2221-finalizers-should-be-protected"></a>CA2221: Finalizer sollten geschützt sein
|||
|-|-|
|TypeName|FinalizersShouldBeProtected|
|CheckId|CA2221|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ implementiert einen Finalizer, der kein (geschützten) Zugriff angegeben ist.

## <a name="rule-description"></a>Regelbeschreibung
 Finalizer müssen den Familienzugriffsmodifizierer verwenden. Diese Regel wird vom C#-, Visual Basic und Visual C++-Compiler erzwungen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Finalizer Familie zugegriffen werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Diese Regel kann nicht in jeder .NET-Sprache auf hoher Ebene verletzt; Es kann verletzt werden, wenn Sie Microsoft Intermediate Language schreiben.

```
// =============== CLASS MEMBERS DECLARATION ===================
//   note that class flags, 'extends' and 'implements' clauses
//          are provided here for information only

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit FinalizeMethodNotProtected
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance void
            Finalize() cil managed
    {

      // Code size       1 (0x1)
      .maxstack  0
      IL_0000:  ret
    } // end of method FinalizeMethodNotProtected::Finalize

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method FinalizeMethodNotProtected::.ctor

  } // end of class FinalizeMethodNotProtected
} // end of namespace
```

## <a name="see-also"></a>Siehe auch
 [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern)