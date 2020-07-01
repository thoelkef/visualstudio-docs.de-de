---
title: 'CA2102: nicht clskompatible Ausnahmen in allgemeinen Handlern abfangen | Microsoft-Dokumentation'
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
ms.openlocfilehash: e2335b6d2bc3a5e99f0e6de1afefac4f42de0501
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521302"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '|
|CheckId|CA2102|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Member in einer Assembly, die nicht mit oder gekennzeichnet ist, <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> `RuntimeCompatibility(WrapNonExceptionThrows = false)` enthält einen catch-Block, der behandelt <xref:System.Exception?displayProperty=fullName> und keinen unmittelbar folgenden allgemeinen catch-Block enthält. Diese Regel ignoriert Assemblys [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

## <a name="rule-description"></a>Beschreibung der Regel
 Ein catch-Block, der behandelt, <xref:System.Exception> fängt alle Common Language Specification (CLS)-kompatible Ausnahmen ab. Es werden jedoch keine nicht CLS-kompatiblen Ausnahmen abgefangen. Nicht CLS-kompatible Ausnahmen können aus nativem Code oder verwaltetem Code ausgelöst werden, der vom MSIL-Assembler (Microsoft Intermediate Language) generiert wurde. Beachten Sie, dass die c#-und [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Compiler nicht zulassen, dass nicht CLS-kompatible Ausnahmen ausgelöst werden, und [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] keine nicht CLS-kompatiblen Ausnahmen abfängt. Wenn die Absicht des catch-Blocks darin besteht, alle Ausnahmen zu behandeln, verwenden Sie die folgende allgemeine catch-Block-Syntax.

- C#: `catch {}`

- C++: `catch(...) {}` oder`catch(Object^) {}`

  Eine nicht behandelte nicht CLS-kompatible Ausnahme wird zu einem Sicherheitsproblem, wenn zuvor zulässige Berechtigungen im catch-Block entfernt wurden. Da nicht CLS-kompatible Ausnahmen nicht abgefangen werden, könnte eine böswillige Methode, die eine nicht CLS-kompatible Ausnahme auslöst, mit erhöhten Berechtigungen ausgeführt werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenn alle Ausnahmen abgefangen werden sollen, ersetzen oder fügen Sie einen allgemeinen catch-Block ein, oder markieren Sie die Assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)` . Wenn Berechtigungen im catch-Block entfernt werden, duplizieren Sie die Funktionalität im allgemeinen catch-Block. Wenn es nicht die Absicht ist, alle Ausnahmen zu behandeln, ersetzen Sie den catch-Block, der durch Catch-Blöcke behandelt wird, <xref:System.Exception> die bestimmte Ausnahme Typen verarbeiten.

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
 [CA1031: Allgemeine Ausnahmetypen nicht auffangen.](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Weitere Informationen
 [Ausnahmen und Ausnahmebehandlung](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (Il-Assembler)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) Überschreiben von [Sicherheitsüberprüfungen](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [Sprachen Unabhängigkeit und sprachunabhängige Komponenten](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
