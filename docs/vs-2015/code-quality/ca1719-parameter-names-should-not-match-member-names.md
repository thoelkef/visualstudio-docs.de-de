---
title: 'CA1719: Parameternamen sollten nicht mit übereinstimmen Elementnamen | Microsoft-Dokumentation'
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
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 74897625a8d8fced4a87a6e5d722d9edf04769b4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828211"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines extern sichtbaren Members übereinstimmt, in einem Groß-/Kleinschreibung Vergleich, der den Namen des einen seiner Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Parameternamen an, der den Namen des Members nicht übereinstimmen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Für neue Entwicklungen keine bekannte Szenarios auftreten, in dem Sie eine Warnung dieser Regel unterdrücken müssen. Um den rückversand für Bibliotheken, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)



