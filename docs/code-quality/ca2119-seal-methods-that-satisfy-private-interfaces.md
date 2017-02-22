---
title: "CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erf&#252;llen | Microsoft Docs"
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
  - "SealMethodsThatSatisfyPrivateInterfaces"
  - "CA2119"
helpviewer_keywords: 
  - "CA2119"
  - "SealMethodsThatSatisfyPrivateInterfaces"
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erf&#252;llen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein vererbbarer öffentlicher Typ stellt eine überschreibbare Methodenimplementierung einer `internal`\-Schnittstelle bereit \(`Friend` in Visual Basic\).  
  
## Regelbeschreibung  
 Schnittstellenmethoden weisen öffentliche Zugriffsmöglichkeiten auf, die durch den Implementierungstyp nicht geändert werden können.  Eine interne Schnittstelle erstellt einen Vertrag, der nicht außerhalb der Assembly, welche die Schnittstelle definiert, implementiert werden soll.  Durch einen öffentlichen Typ, der eine Methode einer internen Schnittstelle mithilfe des `virtual`\-Modifizierers \(`Overridable` in Visual Basic\) implementiert, kann die Methode von einem abgeleiteten Typ, der sich außerhalb der Assembly befindet, überschrieben werden.  Wenn ein zweiter Typ in der definierenden Assembly die Methode aufruft und einen nur intern zu implementierenden Vertrag erwartet, wird das Verhalten möglicherweise beeinträchtigt, wenn stattdessen die überschriebene Methode in der externen Assembly ausgeführt wird.  Auf diese Weise entsteht ein Sicherheitsrisiko.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie mit einem der folgenden Schritte, dass die Methode außerhalb der Assembly überschrieben wird:  
  
-   Erstellen Sie den deklarierenden Typ `sealed` \(`NotInheritable` in Visual Basic\).  
  
-   Ändern Sie die Zugriffsart des deklarierenden Typs in `internal` \(`Friend` in Visual Basic\).  
  
-   Entfernen Sie alle öffentlichen Konstruktoren von dem deklarierenden Typ.  
  
-   Implementieren Sie die Methode ohne den `virtual`\-Modifizierer.  
  
-   Implementieren Sie die Methode explizit.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden, wenn nach sorgfältiger Überprüfung keine Sicherheitslücken mehr vorhanden sind, die ausgenutzt werden können, wenn die Methode außerhalb der Assembly überschrieben wird.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, `BaseImplementation`, der gegen diese Regel verstößt.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-cs[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## Beispiel  
 Im folgenden Beispiel wird die virtuelle Methodenimplementierung des vorherigen Beispiels ausgenutzt.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-cs[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## Siehe auch  
 [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)   
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)