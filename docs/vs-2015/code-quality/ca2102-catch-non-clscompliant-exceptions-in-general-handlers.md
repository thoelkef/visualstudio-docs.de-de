---
title: ': Ca2102 nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1e798f7c8377d0bde569c9c0e1c10cc299b28af6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590326"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2102: nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen](https://docs.microsoft.com/visualstudio/code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers).

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Element in einer Assembly, die nicht mit der <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> oder markiert `RuntimeCompatibility(WrapNonExceptionThrows = false)` enthält einen Catch-Block, der verarbeitet <xref:System.Exception?displayProperty=fullName> und keinen unmittelbar folgenden allgemeinen Catch-Block. Diese Regel ignoriert [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Assemblys.

## <a name="rule-description"></a>Regelbeschreibung
 Ein CatchBlock, behandelt <xref:System.Exception> fängt alle Common Language Specification (CLS) kompatibel Ausnahmen ab. Allerdings ist nicht CLS-kompatiblen Ausnahmen abgefangen werden. Nicht CLS-kompatible Ausnahmen ausgelöst werden können, von nativem Code oder von verwaltetem Code, die von Microsoft generiert wurde, intermediate Language (MSIL) Assembler. Beachten Sie, dass die C#- und [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Compiler lassen nicht nicht mit CLS kompatible Ausnahmen ausgelöst werden und [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] keine nicht-CLS kompatiblen Ausnahmen abgefangen. Ist die Absicht des Catch-Blocks alle Ausnahmen behandeln, verwenden Sie die folgenden allgemeinen Catch-Block Syntax.

-   C#: `catch {}`

-   C++: `catch(...) {}` oder `catch(Object^) {}`

 Eine nicht behandelte nicht CLS-kompatible Ausnahme wird ein Sicherheitsproblem, wenn zuvor zulässige Berechtigungen im Catch-Block entfernt werden. Da nicht CLS-kompatiblen Ausnahmen abgefangen werden, kann eine böswillige-Methode, die eine nicht CLS-kompatible Ausnahme ausgelöst mit erweiterten Berechtigungen ausgeführt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, bei der die Absicht ist, zum Abfangen aller Ausnahmen, ersetzen, oder fügen Sie einen allgemeinen Catch-Block hinzu, oder markieren Sie die Assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Berechtigungen im Catch-Block entfernt, doppelte die Funktionalität in den allgemeinen catch-Block. Ist dies nicht der Absicht, alle Ausnahmen behandeln, ersetzen Sie den Catch-Block, der verarbeitet <xref:System.Exception> Catch-Blöcke, die bestimmte Ausnahmetypen behandelt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn der Try-Block keine Anweisungen enthält, die eine nicht-CLS-kompatible Ausnahme generieren kann. Da alle systemeigenen oder verwalteten Code eine nicht CLS-kompatible Ausnahme ausgelöst werden kann, erfordert dies Kenntnisse des gesamten Codes, die in allen Codepfaden innerhalb des Try-Blocks ausgeführt werden können. Beachten Sie, dass nicht mit CLS kompatiblen Ausnahmen nicht von der common Language Runtime ausgelöst werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine MSIL-Klasse, die eine nicht-CLS-kompatible Ausnahme ausgelöst.

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

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Kompilieren Sie wie folgt in den vorherigen Beispielen.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Verwandte Regeln
 [CA1031: Allgemeine Ausnahmetypen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Siehe auch
 [Ausnahmen und Ausnahmebehandlung](http://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (IL-Assembler)](http://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [Überschreiben von Sicherheitsüberprüfungen](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [Sprachenunabhängigkeit und sprachunabhängige Komponenten](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



