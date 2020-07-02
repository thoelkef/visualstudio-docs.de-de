---
title: 'CA2132: Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 401aa6f5ebec4dac99bedba6f12478c7c48d1dc5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540815"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|Defaultconstructor smusthavekonsistenttransparenz|
|CheckId|CA2132|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

> [!NOTE]
> Diese Warnung wird nur auf Code angewendet, der CoreCLR (die Version der CLR, die für Silverlight-Webanwendungen spezifisch ist) ausgeführt wird.

## <a name="cause"></a>Ursache
 Das Attribut "Transparenz" des Standardkonstruktors einer abgeleiteten Klasse ist nicht so wichtig wie die Transparenz der Basisklasse.

## <a name="rule-description"></a>Beschreibung der Regel
 Typen und Member <xref:System.Security.SecurityCriticalAttribute> mit dem können nicht vom Silverlight-Anwendungscode verwendet werden. Sicherheitsrelevante Typen und Member können nur von vertrauenswürdigem Code in der .NET Framework for Silverlight-Klassenbibliothek verwendet werden. Da eine öffentliche oder geschützte Konstruktion in einer abgeleiteten Klasse mindestens die gleiche Transparenz aufweisen muss wie die zugehörige Basisklasse, können Klassen in einer Anwendung nicht von Klassen abgeleitet werden, die als SecurityCritical markiert sind.

 Wenn ein Basistyp über einen öffentlichen oder geschützten, nicht transparenten Standardkonstruktor verfügt, muss der abgeleitete Typ den standardkonstruktorvererbungs Regeln für den CoreCLR-Platt Form Code entsprechen. Der abgeleitete Typ muss auch über einen Standardkonstruktor verfügen, und dieser Konstruktor muss mindestens dem kritischen Standardkonstruktor des Basistyps sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie zum Beheben des Verstoßes den Typ, oder leiten Sie nicht vom nicht transparenten Sicherheits Typ ab.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Warnungen von dieser Regel nicht unterdrücken. Verstöße gegen diese Regel durch den Anwendungscode führen dazu, dass die CoreCLR den Typ mit einem ablehnt <xref:System.TypeLoadException> .

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Kommentare
