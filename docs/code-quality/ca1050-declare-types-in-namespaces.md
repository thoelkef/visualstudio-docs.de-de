---
title: 'CA1050: Typen in Namespaces deklarieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 297491e6f3bdaef2b0d460bfe37716f6cae0dbd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Typen in Namespaces deklarieren
|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter Typ ist außerhalb des Bereichs eines benannten Namespaces definiert.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Typen werden in Namespaces, um Namenskonflikte zu verhindern und als eine Möglichkeit, verwandte Typen in einer Objekthierarchie zu organisieren deklariert. Typen, die außerhalb eines benannten Namespaces befinden sich in einen globalen Namespace, der im Code verwiesen werden kann.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, platzieren Sie den Typ in einem Namespace.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Obwohl Sie nie zum Unterdrücken einer Warnung dieser Regel müssen, ist es sicher, dieses Verfahren, wenn die Assembly nie zusammen mit anderen Assemblys verwendet werden soll.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, eine Bibliothek, deren Typ falsch außerhalb eines Namespace deklariert und ein Typ, der den gleichen Namen in einem Namespace deklariert hat.  
  
 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## <a name="example"></a>Beispiel  
 Die folgende Anwendung verwendet die Bibliothek, die zuvor definiert wurde. Beachten Sie, dass der Typ, der außerhalb eines Namespace deklariert wird erstellt wird der Name `Test` ist nicht mit einem Namespace qualifiziert. Beachten Sie auch den Zugriff auf die `Test` geben `Goodspace`, der Namespacename ist erforderlich.  
  
 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]