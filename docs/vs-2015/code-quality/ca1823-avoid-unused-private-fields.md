---
title: 'CA1823: Nicht verwendete private Felder vermeiden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bfe51ab6c163c82d413c5c7cc74edc0b980abd85
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47524989"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Nicht verwendete private Felder vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1823: nicht verwendete private Felder vermeiden](https://docs.microsoft.com/visualstudio/code-quality/ca1823-avoid-unused-private-fields).

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Mit dieser Regel wird gemeldet, wenn ein privates Feld in Ihrem Code vorhanden ist, jedoch nicht von jedem Codepfad verwendet werden.

## <a name="rule-description"></a>Regelbeschreibung
 Es wurden private Felder erkannt, auf die in der Assembly anscheinend kein Zugriff erfolgt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Feld, oder fügen Sie Code, der verwendet wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)



