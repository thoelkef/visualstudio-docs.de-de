---
title: 'CA1050: Typen in Namespaces deklarieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5bff984d9ea11ba8fd7f2e42deb5898f04da7d44
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548482"
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
 Typen werden in Namespaces, um Namenskonflikte zu verhindern und als eine Möglichkeit zum Organisieren verwandter Typen in einer Objekthierarchie deklariert. Typen, die außerhalb eines benannten Namespaces sind in einem globalen Namespace, der nicht im Code verwiesen werden kann.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, platzieren Sie den Typ in einem Namespace.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Obwohl Sie nie eine Warnung dieser Regel unterdrücken verfügen, ist es sicher ist, die dies tun, wenn die Assembly nicht zusammen mit anderen Assemblys verwendet werden soll.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Bibliothek, die ein Typ, der falsch außerhalb eines Namespaces deklariert hat, und ein Typ, der den gleichen Namen, die in einem Namespace deklariert hat.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung verwendet die Bibliothek, die zuvor definiert wurde. Beachten Sie, dass der Typ, der außerhalb eines Namespace deklariert wird, wenn erstellt wird der Name `Test` wird nicht durch einen Namespace gekennzeichnet. Beachten Sie außerdem, den Zugriff auf die `Test` geben `Goodspace`, der Namespacename ist erforderlich.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_2.cs)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_2.vb)]