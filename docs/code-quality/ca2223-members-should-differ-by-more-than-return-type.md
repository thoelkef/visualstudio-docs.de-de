---
title: "CA2223: Member sollten sich durch mehr als nur den R&#252;ckgabetyp unterscheiden | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MembersShouldDifferByMoreThanReturnType"
  - "CA2223"
helpviewer_keywords: 
  - "CA2223"
  - "MembersShouldDifferByMoreThanReturnType"
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2223: Member sollten sich durch mehr als nur den R&#252;ckgabetyp unterscheiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldDifferByMoreThanReturnType|  
|CheckId|CA2223|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Zwei öffentliche oder geschützte Member weisen Signaturen auf, die bis auf den Rückgabetyp identisch sind.  
  
## Regelbeschreibung  
 Die Common Language Runtime lässt die Verwendung von Rückgabetypen zu, mit deren Hilfe zwischen anderweitig identischen Membern unterschieden werden kann. Trotzdem ist dieses Feature weder in der Common Language Specification \(CLS\) enthalten, noch eine gebräuchliche Funktion von .NET\-Programmiersprachen.  Wenn sich Member nur durch den Rückgabetyp unterscheiden, sind Entwickler und Entwicklungstools möglicherweise nicht in der Lage, sie richtig zu unterscheiden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Gestaltung der Member so, dass sie ausschließlich aufgrund ihrer Namen und Parametertypen unverwechselbar sind, oder Sie machen die Member nicht verfügbar.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel \(in Microsoft Intermediate Language, MSIL\), wird ein Typ veranschaulicht, der gegen diese Regel verstößt.  Beachten Sie, dass mit C\# oder Visual Basic .NET nicht gegen diese Regel verstoßen werden kann.  
  
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