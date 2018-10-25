---
title: 'CA2222: Sichtbarkeit für geerbte Member nicht verringern | Microsoft-Dokumentation'
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
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8bc4ff141e48554e631b2163afd64e7935f50c5b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837749"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Sichtbarkeit für geerbte Member nicht verringern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine private Methode in einem nicht versiegelten Typ verfügt über eine Signatur, die an eine öffentliche Methode, die in einem Basistyp deklariert identisch ist. Die private Methode ist nicht endgültig.

## <a name="rule-description"></a>Regelbeschreibung
 Sie sollten den Zugriffsmodifizierer für geerbte Member nicht ändern. Wenn Sie einen geerbten Member in private ändern, werden Aufrufer nicht am Zugriff auf die Implementierung der Basisklasse der Methode gehindert. Wenn das Element ist privat, und der Typ nicht versiegelten ist, kann durch das erbende Typen die letzte öffentliche Implementierung der Methode in der Vererbungshierarchie aufrufen. Wenn Sie den Zugriffsmodifizierer ändern müssen, die Methode sollte als final gekennzeichnet werden, oder sein Typ muss versiegelt werden, um zu verhindern, dass die Methode überschrieben wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Zugriff auf nicht privat sein. Auch wenn Ihre bevorzugte Programmiersprache unterstützt wird, können Sie die Methode endgültige vornehmen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]



