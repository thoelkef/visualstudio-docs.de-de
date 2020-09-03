---
title: 'CA2131: sicherheitskritische Typen dürfen nicht an typäquivalenz beteiligt sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ccd556a5929e56597de678ad4ad8ea6c101b7c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535888"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|Criticaltypesmustnotparticipateingetypeäquivalenz|
|CheckId|CA2131|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ ist an typäquivalenz beteiligt, und der Typ selbst oder ein Member oder Feld des Typs ist mit dem-Attribut gekennzeichnet <xref:System.Security.SecurityCriticalAttribute> .

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel wird für alle wichtigen Typen ausgelöst oder für Typen, die wichtige Methoden oder Felder enthalten, die an der Typäquivalenz beteiligt sind. Wenn die CLR einen solchen Typ erkennt, kann Sie zur Laufzeit nicht mit einem geladen werden <xref:System.TypeLoadException> . In der Regel wird diese Regel nur ausgelöst, wenn Benutzer Typäquivalenz manuell implementieren und die Typäquivalenz nicht von tlbimp und den Compilern ausführen lassen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie das SecurityCritical-Attribut, um einen Verstoß gegen diese Regel zu beheben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die folgenden Beispiele veranschaulichen eine Schnittstelle, eine Methode und ein Feld, das dazu führt, dass diese Regel ausgelöst wird.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 [Sicherheitstransparenter Code, Ebene 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
