---
title: 'CA1050: Typen in Namespaces deklarieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f13684df70db7026e874bc8edb6282faca2cf98d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200541"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Typen in Namespaces deklarieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ ist außerhalb des Bereichs eines benannten Namespaces definiert.

## <a name="rule-description"></a>Regelbeschreibung
 Typen werden in Namespaces, um Namenskonflikte zu verhindern und als eine Möglichkeit zum Organisieren verwandter Typen in einer Objekthierarchie deklariert. Typen, die außerhalb eines benannten Namespaces sind in einem globalen Namespace, der nicht im Code verwiesen werden kann.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, platzieren Sie den Typ in einem Namespace.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Obwohl Sie nie eine Warnung dieser Regel unterdrücken verfügen, ist es sicher ist, die dies tun, wenn die Assembly nicht zusammen mit anderen Assemblys verwendet werden soll.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Bibliothek, die ein Typ, der falsch außerhalb eines Namespaces deklariert hat, und ein Typ, der den gleichen Namen, die in einem Namespace deklariert hat.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung verwendet die Bibliothek, die zuvor definiert wurde. Beachten Sie, dass der Typ, der außerhalb eines Namespace deklariert wird, wenn erstellt wird der Name `Test` wird nicht durch einen Namespace gekennzeichnet. Beachten Sie außerdem, den Zugriff auf die `Test` geben `Goodspace`, der Namespacename ist erforderlich.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
