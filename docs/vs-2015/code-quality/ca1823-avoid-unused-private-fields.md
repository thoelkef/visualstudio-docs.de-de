---
title: 'CA1823: nicht verwendete private Felder vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 01f2ef59ceb6d10cc33276fdd3e5388f39175f8b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545300"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Nicht verwendete private Felder vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Diese Regel wird gemeldet, wenn ein privates Feld im Code vorhanden ist, aber nicht von einem Codepfad verwendet wird.

## <a name="rule-description"></a>Beschreibung der Regel
 Es wurden private Felder erkannt, auf die in der Assembly anscheinend kein Zugriff erfolgt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Feld, oder fügen Sie Code hinzu, der es verwendet.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1812: Nicht instanziierte interne Klassen vermeiden.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Nicht verwendete Parameter überprüfen.](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen.](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: Nicht aufgerufenen privaten Code vermeiden.](../code-quality/ca1811-avoid-uncalled-private-code.md)
