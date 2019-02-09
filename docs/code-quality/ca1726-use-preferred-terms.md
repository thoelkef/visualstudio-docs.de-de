---
title: 'CA1726: Bevorzugte Begriffe verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 469025e5856f284f4d8887b351865a0304e4d35c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55917311"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Bevorzugte Begriffe verwenden.

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Wichtige – Wenn ausgelöst von Assemblys<br /><br /> Nicht unterbrechend – Wenn ausgelöst von Typparametern|

## <a name="cause"></a>Ursache

Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Oder der Name enthält den Begriff Flag oder Flags.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel analysiert einen Bezeichner in Token. Jedes einzelne Token und jeder Kombination aus zwei zusammenhängende token wird mit Begriffen verglichen, die in der Regel und im Abschnitt "veraltet" des benutzerdefinierten Wörterbüchern erstellt werden. Die folgende Tabelle zeigt die Bedingungen, die in der Regel, und ihre bevorzugten Alternativen integriert sind.

|Veraltete Bezeichnung|Bevorzugter Begriff|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` oder `Flags`|Es gibt keine ersetzungsbegriff. Nicht verwenden.|
|`Hadnt`|`HadNot`|
|`Hasnt`|`HasNot`|
|`Havent`|`HaveNot`|
|`Indices`|`Indexes`|
|`Isnt`|`IsNot`|
|`LogIn`|`LogOn`|
|`LogOut`|`LogOff`|
|`Shouldnt`|`ShouldNot`|
|`SignOn`|`SignIn`|
|`SignOff`|`SignOut`|
|`Wasnt`|`WasNot`|
|`Werent`|`WereNot`|
|`Wont`|`WillNot`|
|`Wouldnt`|`WouldNot`|
|`Writeable`|`Writable`|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Begriff mit dem bevorzugten Begriff für die alternative.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn der Name des Bezeichners beabsichtigt ist und bezieht sich speziell auf dem ursprünglichen Begriff dem bevorzugten Begriff.

## <a name="related-rules"></a>Verwandte Regeln
 [Benennungswarnungen](../code-quality/naming-warnings.md)