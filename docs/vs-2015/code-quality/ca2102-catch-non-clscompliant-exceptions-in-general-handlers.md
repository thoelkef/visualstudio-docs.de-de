---
title: 'CA2102: Nicht CLS-kompatible Ausnahmen in allgemeinen Handlern abfangen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 051b59183a761477476269480ecdf83ccbf0cb37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652176"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '|
|CheckId|CA2102|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Member in einer Assembly, der nicht mit dem <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> gekennzeichnet ist oder `RuntimeCompatibility(WrapNonExceptionThrows = false)` markiert ist, enthält einen catch-Block, der <xref:System.Exception?displayProperty=fullName> verarbeitet und keinen unmittelbar folgenden allgemeinen catch-Block enthält. Diese Regel ignoriert [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Assemblys.

## <a name="rule-description"></a>Regelbeschreibung
 Ein catch-Block, der <xref:System.Exception> behandelt, fängt alle Common Language Specification (CLS) kompatiblen Ausnahmen ab. Es werden jedoch keine nicht CLS-kompatiblen Ausnahmen abgefangen. Nicht CLS-kompatible Ausnahmen können aus nativem Code oder verwaltetem Code ausgelöst werden, der vom MSIL-Assembler (Microsoft Intermediate Language) generiert wurde. Beachten Sie, C# dass die-und-[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]-Compiler nicht zulassen, dass nicht CLS-kompatible Ausnahmen ausgelöst werden, und [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] keine nicht CLS-kompatiblen Ausnahmen abfängt. Wenn die Absicht des catch-Blocks darin besteht, alle Ausnahmen zu behandeln, verwenden Sie die folgende allgemeine catch-Block-Syntax.

- C#: `catch {}`

- C++: `catch(...) {}` oder `catch(Object^) {}`

  Eine nicht behandelte nicht CLS-kompatible Ausnahme wird zu einem Sicherheitsproblem, wenn zuvor zulässige Berechtigungen im catch-Block entfernt wurden. Da nicht CLS-kompatible Ausnahmen nicht abgefangen werden, könnte eine böswillige Methode, die eine nicht CLS-kompatible Ausnahme auslöst, mit erhöhten Berechtigungen ausgeführt werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenn alle Ausnahmen abgefangen werden sollen, ersetzen oder fügen Sie einen allgemeinen catch-Block ein, oder markieren Sie die Assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Wenn Berechtigungen im catch-Block entfernt werden, duplizieren Sie die Funktionalität im allgemeinen catch-Block. Wenn es nicht die Absicht ist, alle Ausnahmen zu behandeln, ersetzen Sie den catch-Block, der <xref:System.Exception> behandelt, durch Catch-Blöcke, die bestimmte Ausnahme Typen verarbeiten.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der try-Block keine Anweisungen enthält, die möglicherweise eine nicht CLS-kompatible Ausnahme generieren. Da nativer oder verwalteter Code möglicherweise eine nicht CLS-kompatible Ausnahme auslöst, erfordert dies das Wissen über den gesamten Code, der in allen Codepfade innerhalb des try-Blocks ausgeführt werden kann. Beachten Sie, dass nicht CLS-kompatible Ausnahmen nicht vom Common Language Runtime ausgelöst werden.

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
 Das folgende Beispiel zeigt eine-Methode, die einen allgemeinen catch-Block enthält, der die Regel erfüllt.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Kompilieren Sie die vorherigen Beispiele wie folgt.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Verwandte Regeln
 [CA1031: Allgemeine Ausnahme Typen nicht auffangen ](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Siehe auch
 [Ausnahmen und Ausnahmebehandlung](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) von [Ilasm. exe (Il-Assembler)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [außer Kraft setzung der](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [Sprachunabhängigkeit und sprachunabhängige Komponenten](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
