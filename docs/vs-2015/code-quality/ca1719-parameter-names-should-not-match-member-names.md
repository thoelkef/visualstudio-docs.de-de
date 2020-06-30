---
title: 'CA1719: Parameter Namen sollten nicht mit Elementnamen identisch sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5024d2ddb7f31593c8eaedfc2fb421b4a0e9b0a4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545365"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines extern sichtbaren Elements entspricht dem Vergleich ohne Beachtung der Groß-/Kleinschreibung dem Namen eines seiner Parameter.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Parameternamen aus, der nicht mit dem Elementnamen identisch ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Bei der neuen Entwicklung treten keine bekannten Szenarien auf, in denen Sie eine Warnung aus dieser Regel unterdrücken müssen. Bei Versand Bibliotheken müssen Sie möglicherweise eine Warnung aus dieser Regel unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
