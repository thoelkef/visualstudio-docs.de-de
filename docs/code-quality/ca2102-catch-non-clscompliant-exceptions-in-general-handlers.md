---
title: "CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102: Nicht-CLSCompliant-Ausnahmen in allgemeinen Handlern abfangen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Member in einer Assembly, die nicht mit <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> gekennzeichnet ist bzw. mit `RuntimeCompatibility(WrapNonExceptionThrows = false)` gekennzeichnet ist, enthält einen catch\-Block zur Behandlung von <xref:System.Exception?displayProperty=fullName> und keinen unmittelbar folgenden allgemeinen catch\-Block.  Diese Regel ignoriert [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Assemblys.  
  
## Regelbeschreibung  
 Ein catch\-Block, der <xref:System.Exception> behandelt, fängt alle CLS \(Common Language Specification\-\)kompatiblen Ausnahmen ab.  Nicht CLS\-kompatible Ausnahmen werden jedoch nicht abgefangen.  Nicht CLS\-kompatible Ausnahmen können von systemeigenem Code oder verwaltetem Code ausgelöst werden, der vom MSIL \(Microsoft Intermediate Language\)\-Assembler generiert wird.  Beachten Sie, dass der C\#\- und der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler das Auslösen nicht CLS\-kompatibler Ausnahmen nicht gestatten und dass [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] keine nicht CLS\-kompatiblen Ausnahmen abfängt.  Falls mit dem catch\-Block alle Ausnahmen behandelt werden sollen, verwenden Sie die folgende allgemeine Syntax für catch\-Blöcke.  
  
-   C\#: `catch {}`  
  
-   C\+\+: `catch(...) {}` oder `catch(Object^) {}`  
  
 Eine unbehandelte nicht CLS\-kompatible Ausnahme wird zu einem Sicherheitsrisiko, wenn früher zulässige Berechtigungen aus dem catch\-Block entfernt werden.  Da nicht CLS\-kompatible Ausnahmen nicht abgefangen werden, könnte eine böswillige Methode, die eine nicht CLS\-kompatible Ausnahme auslöst, mit erhöhten Berechtigungen ausgeführt werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, während der Zweck darin besteht, alle Ausnahmen abzufangen, ersetzen oder fügen Sie einen allgemeinen catch\-Block hinzu oder markieren die Assembly als `RuntimeCompatibility(WrapNonExceptionThrows = true)`.  Wenn Berechtigungen im catch\-Block entfernt werden, duplizieren Sie die Funktionalität im allgemeinen catch\-Block.  Falls der Zweck nicht darin besteht, alle Ausnahmen zu behandeln, ersetzen Sie den catch\-Block, durch den <xref:System.Exception> behandelt wird, durch catch\-Blöcke zur Behandlung spezifischer Ausnahmetypen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der try\-Block keine Anweisungen enthält, durch die eine nicht CLS\-kompatible Ausnahme generiert werden könnte.  Da eine nicht CLS\-kompatible Ausnahme durch beliebigen systemeigenen oder verwalteten Code ausgelöst werden kann, ist hier die grundlegende Kenntnis sämtlichen Codes erforderlich, der in allen Codepfaden innerhalb des try\-Blocks ausgeführt werden kann.  Beachten Sie, dass nicht CLS\-kompatible Ausnahmen nicht von der Common Language Runtime ausgelöst werden.  
  
## Beispiel  
 Im folgenden Beispiel wird eine MSIL\-Klasse veranschaulicht, die eine nicht CLS\-kompatible Ausnahme auslöst.  
  
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
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode veranschaulicht, die einen allgemeinen catch\-Block enthält, der die Regel erfüllt.  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Kompilieren Sie die vorherigen Beispiele wie folgt.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## Verwandte Regeln  
 [CA1031: Allgemeine Ausnahmetypen nicht auffangen](../code-quality/ca1031-do-not-catch-general-exception-types.md)  
  
## Siehe auch  
 [Ausnahmen und Ausnahmebehandlung](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe \(IL Assembler\)](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/de-de/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)