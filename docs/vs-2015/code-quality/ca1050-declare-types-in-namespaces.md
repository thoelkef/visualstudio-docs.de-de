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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c56de70daeabd05215f68024339d5855686d529b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653834"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: Typen in Namespaces deklarieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ wird außerhalb des Gültigkeits Bereichs eines benannten Namespace definiert.

## <a name="rule-description"></a>Regelbeschreibung
 Typen werden in Namespaces deklariert, um Namenskonflikte zu verhindern, und als Möglichkeit, verwandte Typen in einer Objekthierarchie zu organisieren. Typen, die sich außerhalb eines benannten Namespace befinden, befinden sich in einem globalen Namespace, auf den im Code nicht verwiesen werden kann.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, platzieren Sie den-Typ in einem Namespace.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Obwohl Sie eine Warnung nicht von dieser Regel unterdrücken müssen, ist dies sicher, wenn die Assembly nicht in Verbindung mit anderen Assemblys verwendet wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Bibliothek, die einen Typ aufweist, der fälschlicherweise außerhalb eines Namespaces deklariert wurde, und einen Typ, der denselben Namen aufweist, der in einem Namespace deklariert wurde.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung verwendet die zuvor definierte Bibliothek. Beachten Sie, dass der Typ, der außerhalb eines Namespaces deklariert ist, erstellt wird, wenn der Name `Test` nicht durch einen Namespace qualifiziert ist. Beachten Sie auch, dass der Namespace Name erforderlich ist, um auf den `Test` Typ in `Goodspace` zuzugreifen.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
