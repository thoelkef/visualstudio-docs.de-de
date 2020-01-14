---
title: 'CA1726: bevorzugte Begriffe verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 639a42e26442e31f7bbbbb2245af0289c6a04fd8
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918228"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Bevorzugte Begriffe verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1726: bevorzugte Begriffe verwenden](/visualstudio/code-quality/ca1726-use-preferred-terms).

|||
|-|-|
|TypeName|UsePreferredTerms|
|CheckId|CA1726|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechen: beim Auslösen für Assemblys<br /><br /> Nicht unterbrechend: beim Auslösen für Typparameter|

## <a name="cause"></a>Ursache
 Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Alternativ enthält der Name den Begriff Flag oder Flags.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel analysiert einen Bezeichner in Token. Jedes einzelne Token und jede zusammenhängende Kombination aus Dual Token wird mit Begriffen verglichen, die in die Regel und im veralteten Abschnitt von benutzerdefinierten Wörterbüchern integriert sind. In der folgenden Tabelle sind die Begriffe, die in die Regel integriert sind, und Ihre bevorzugten Alternativen aufgeführt.

|Veralteter Begriff|Bevorzugter Begriff|
|-------------------|--------------------|
|`Arent`|`AreNot`|
|`Cancelled`|`Canceled`|
|`Cant`|`Cannot`|
|`ComPlus`|`EnterpriseServices`|
|`Couldnt`|`CouldNot`|
|`Didnt`|`DidNot`|
|`Doesnt`|`DoesNot`|
|`Dont`|`DoNot`|
|`Flag` oder `Flags`|Es gibt keinen Ersetzungs Begriff. Nicht verwenden.|
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
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Begriff durch den bevorzugten Alternativen Begriff.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel nur, wenn der Name des Bezeichners beabsichtigt ist und sich nicht auf den bevorzugten Begriff, sondern speziell auf den ursprünglichen Begriff bezieht.

## <a name="related-rules"></a>Verwandte Regeln
 [Benennungswarnungen](../code-quality/naming-warnings.md)
