---
title: 'CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb13b2b74ca86101949275e418968e577ca2b7c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Virtuelle Member in versiegelten Typen nicht deklarieren
|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher Typ ist versiegelt und deklariert eine Methode, die sowohl `virtual` (`Overridable` in Visual Basic) und nicht die letzte. Diese Regel meldet keine Verstöße für Delegattypen, die diesem Muster folgen müssen.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Typen deklarieren Methoden als virtuell, damit erbende Typen die Implementierung der virtuellen Methode überschreiben können. Sie können nicht per Definition aus einem versiegelten Typ, indem eine virtuelle Methode für einen versiegelten Typ bedeutungslos erben.  
  
 Die Visual Basic .NET und C#-Compiler lassen sich nicht auf Typen, die diese Regel verletzen aus.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die Methode nicht virtuell oder nutzen Sie vererbbar.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Verlassen den Typ im aktuellen Zustand kann dazu führen, dass Problemen bei der Wartung und bietet keine Vorteile.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der mit dieser Regel verletzt.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]