---
title: "CA1047: Geschützte Member in versiegelten Typen nicht deklarieren | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: abdde6524f179cff3a1dd368cf218a91499f5381
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Geschützte Member in versiegelten Typen nicht deklarieren
|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher Typ ist `sealed` (`NotInheritable` in Visual Basic) und ein geschützter Member oder einen geschützten geschachtelten Typ deklariert. Diese Regel meldet keine Verstöße für <xref:System.Object.Finalize%2A> -Methoden, die diesem Muster folgen müssen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Typen deklarieren geschützte Member, damit erbende Typen auf den Member zugreifen oder diesen überschreiben können. Per Definition können nicht Sie von einem versiegelten Typ erben, d. h., die geschützten Methoden für versiegelte Typen nicht aufgerufen werden kann.  
  
 Der C#-Compiler gibt eine Warnung für diesen Fehler.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene des Members in private, oder machen Sie den Typ vererbbar.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Verlassen den Typ im aktuellen Zustand kann dazu führen, dass Problemen bei der Wartung und bietet keine Vorteile.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der mit dieser Regel verletzt.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]