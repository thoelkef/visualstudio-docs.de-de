---
title: 'CA2119: Methoden versiegeln, private Schnittstellen erfüllen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c6d3e102cde1fc010f777006d629fa2d19add894
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825392"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Methoden versiegeln, die die Bedingungen privater Schnittstellen erfüllen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein vererbbarer öffentlicher Typ stellt eine überschreibbare methodenimplementierung einer `internal` (`Friend` in Visual Basic) Schnittstelle.

## <a name="rule-description"></a>Regelbeschreibung
 Schnittstellenmethoden müssen Öffentliche zugreifbarkeit, durch den implementierenden Typ kann nicht geändert werden. Eine interne Schnittstelle erstellt einen Vertrag, der nicht vorgesehen ist, außerhalb der Assembly implementiert werden, die die Schnittstelle definiert. Ein öffentlicher Typ, der implementiert eine Methode von einer internen Schnittstelle mithilfe der `virtual` (`Overridable` in Visual Basic)-Modifizierers können die Methode, die von einem abgeleiteten Typ überschrieben werden, die außerhalb der Assembly ist. Wenn Sie ein zweiter Typ in der definierenden Assembly, die Methode aufruft und erwartet, dass einen Vertrag nur intern, möglicherweise Verhalten beeinträchtigt, wenn stattdessen die überschriebene Methode in der externen Assembly ausgeführt wird. Dadurch wird ein Sicherheitsrisiko erstellt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verhindern Sie, dass die Methode außerhalb der Assembly überschrieben wird, indem Sie eine der folgenden:

-   Ändern Sie den deklarierenden Typ `sealed` (`NotInheritable` in Visual Basic).

-   Ändern Sie den Zugriff des deklarierenden Typs `internal` (`Friend` in Visual Basic).

-   Entfernen Sie alle öffentliche Konstruktoren, von dem deklarierenden Typ.

-   Implementieren Sie die Methode ohne Verwendung der `virtual` Modifizierer.

-   Implementieren Sie explizit die Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicherer, unterdrücken Sie eine Warnung von dieser Regel, wenn Sie nach sorgfältiger Prüfung keine Sicherheitsprobleme, die vorhanden sein kann ausgenutzt werden, wenn die Methode außerhalb der Assembly überschrieben wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, `BaseImplementation`, die gegen diese Regel verstößt.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Beispiel
 Im folgende Beispiel nutzt die virtuelle Methode-Implementierung des vorherigen Beispiels.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Schnittstellen](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [Schnittstellen](http://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)



