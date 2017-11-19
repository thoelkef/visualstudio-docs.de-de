---
title: "CA2119: Methoden versiegeln, die privater Schnittstellen erfüllen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f05b59ffc48b072d1a94ddfd405072d9663e6257
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen
|||  
|-|-|  
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|  
|CheckId|CA2119|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein vererbbarer öffentlicher Typ stellt eine überschreibbare methodenimplementierung einer `internal` (`Friend` in Visual Basic) Schnittstelle.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Schnittstellenmethoden haben öffentlichen Zugriff, der den Implementierungstyp nicht geändert werden kann. Eine interne Schnittstelle erstellt einen Vertrag, der nicht außerhalb der Assembly, die die Schnittstelle definiert, implementiert werden sollen. Ein öffentlicher Typ, der implementiert eine Methode von einer internen Schnittstelle mithilfe der `virtual` (`Overridable` in Visual Basic)-Modifizierer ermöglicht die Methode, die von einem abgeleiteten Typ überschrieben werden, die außerhalb der Assembly ist. Wenn ein zweiten Typ in der definierenden Assembly die Methode aufruft und erwartet, einen internes Vertrag dass, möglicherweise Verhalten beeinträchtigt, wenn stattdessen die überschriebene Methode in der externen Assembly ausgeführt wird. Dadurch wird ein Sicherheitsrisiko erstellt.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie, dass die Methode außerhalb der Assembly überschrieben wird, indem Sie eine der folgenden:  
  
-   Den deklarierenden Typ stellen `sealed` (`NotInheritable` in Visual Basic).  
  
-   Ändern Sie den Zugriff des deklarierenden Typs zu `internal` (`Friend` in Visual Basic).  
  
-   Entfernen Sie alle öffentliche Konstruktoren aus der deklarierende Typ.  
  
-   Implementieren Sie die Methode ohne Verwendung der `virtual` Modifizierer.  
  
-   Implementieren Sie die Methode explizit an.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung von diesem kann gefahrlos Regel, wenn nach sorgfältiges überprüfen keine Sicherheitsprobleme, die vorhanden sein, kann ausgenutzt werden, wenn die Methode außerhalb der Assembly überschrieben wird.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ `BaseImplementation`, gegen diese Regel.  
  
 [!code-cpp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_1.cpp)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_1.cs)]
 [!code-vb[FxCop.Security.SealMethods1#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_1.vb)]  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird die Implementierung der virtuellen Methode im vorherigen Beispiel genutzt.  
  
 [!code-cpp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CPP/ca2119-seal-methods-that-satisfy-private-interfaces_2.cpp)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/CSharp/ca2119-seal-methods-that-satisfy-private-interfaces_2.cs)]
 [!code-vb[FxCop.Security.SealMethods2#1](../code-quality/codesnippet/VisualBasic/ca2119-seal-methods-that-satisfy-private-interfaces_2.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)   
 [Schnittstellen](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)