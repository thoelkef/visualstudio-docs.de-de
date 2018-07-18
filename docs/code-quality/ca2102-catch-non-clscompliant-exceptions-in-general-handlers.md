---
title: 'CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f32e6fa3d1dfc3c8ee0f116a6e06de49c90ea256
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916433"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen
|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Element in einer Assembly, die nicht mit der <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> oder markiert `RuntimeCompatibility(WrapNonExceptionThrows = false)` enthält einen CatchBlock, behandelt <xref:System.Exception?displayProperty=fullName> und keinen unmittelbar folgenden allgemeinen Catch-Block. Diese Regel ignoriert [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Assemblys.

## <a name="rule-description"></a>Regelbeschreibung
 Ein CatchBlock, behandelt <xref:System.Exception> alle Common Language Specification (CLS) kompatibel Ausnahmen abfängt. Allerdings ist es nicht nicht CLS-kompatible Ausnahmen abfangen. Nicht CLS-kompatible Ausnahmen ausgelöst werden können, vom systemeigenen Code oder von verwaltetem Code, der von der Microsoft intermediate Language (MSIL) Assembler. Beachten Sie, dass die C#- und [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Compiler nicht zulassen nicht CLS-kompatible Ausnahmen ausgelöst werden und [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keine Ausnahmen nicht CLS-kompatibel. Ist die Absicht des Catch-Blocks alle Ausnahmen behandeln, verwenden Sie die folgenden allgemeinen Catch-Block-Syntax.

-   C#: `catch {}`

-   C++: `catch(...) {}` oder `catch(Object^) {}`

 Eine nicht behandelte nicht CLS-kompatible Ausnahme wird ein Sicherheitsproblem, wenn zuvor zulässige Berechtigungen im Catch-Block entfernt werden. Da nicht CLS kompatibler Ausnahmen abgefangen werden, könnte eine böswillige Methode, die ein nicht CLS-kompatible Ausnahme auslöst mit erweiterten Berechtigungen ausführen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenn die Absicht ist, alle abzufangen Ausnahmen, ersetzen oder fügen Sie einen allgemeinen Catch-Block hinzu oder markieren Sie die Assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Berechtigungen im Catch-Block entfernt, doppelte für die Funktionen in den allgemeinen catch-Block. Ist dies nicht der Absicht, die alle Ausnahmen behandeln, ersetzen Sie die CatchBlock, behandelt <xref:System.Exception> Catch-Blöcke, die bestimmte Ausnahmetypen behandelt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn der Try-Block keine Anweisungen enthalten, die eine nicht CLS-kompatible Ausnahme generieren kann. Da alle systemeigenen oder verwalteten Code eine nicht CLS-kompatible Ausnahme auslösen kann, erfordert dies Kenntnisse der gesamte Code, der in allen Codepfaden innerhalb des Try-Blocks ausgeführt werden kann. Beachten Sie, dass nicht CLS-kompatible Ausnahmen nicht von der common Language Runtime ausgelöst werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine MSIL-Klasse, die eine nicht CLS-kompatible Ausnahme auslöst.

```
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die einen allgemeinen Catch-Block enthält, der die Regel erfüllt.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

 Kompilieren Sie die vorherigen Beispiele wie folgt.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Verwandte Regeln
 [CA1031: Allgemeine Ausnahmetypen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Siehe auch
 [Ausnahmen und Ausnahmebehandlung](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling) [Ilasm.exe (IL-Assembler)](/dotnet/framework/tools/ilasm-exe-il-assembler) [Sprachenunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)