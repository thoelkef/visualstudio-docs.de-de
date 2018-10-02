---
title: 'CA2132: Standardkonstruktoren müssen mindestens genauso kritisch sein wie die Standardkonstruktoren des Basistyps sein | Microsoft-Dokumentation'
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
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ecf78792e18df4956fa0147754879fb2e80648bc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590309"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Standardkonstruktoren müssen mindestens so kritisch sein wie die Standardkonstruktoren des Basistyps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2132: Standardkonstruktoren müssen mindestens genauso kritisch sein wie die Standardkonstruktoren des Basistyps sein](https://docs.microsoft.com/visualstudio/code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors).

|||
|-|-|
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

> [!NOTE]
>  Diese Warnung wird nur auf Code angewendet werden, die die CoreCLR (die Version der CLR, die speziell für Silverlight-Webanwendungen ist) ausgeführt wird.

## <a name="cause"></a>Ursache
 Das Transparenzattribut des Standardkonstruktors einer abgeleiteten Klasse ist nicht so wichtig wie die Transparenz der Basisklasse.

## <a name="rule-description"></a>Regelbeschreibung
 Typen und Member, die die <xref:System.Security.SecurityCriticalAttribute> kann nicht vom Silverlight-Anwendungscode verwendet werden. Sicherheitsrelevante Typen und Member können nur von vertrauenswürdigem Code in der .NET Framework for Silverlight-Klassenbibliothek verwendet werden. Da eine öffentliche oder geschützte Konstruktion in einer abgeleiteten Klasse mindestens die gleiche Transparenz aufweisen muss wie die zugehörige Basisklasse, können Klassen in einer Anwendung nicht von Klassen abgeleitet werden, die als SecurityCritical markiert sind.

 Für CoreCLR-Plattform-Code Wenn ein Basistyp einen öffentlichen oder geschützten nicht transparentes Standardkonstruktor verfügt muss klicken Sie dann der abgeleitete Typ die Vererbungsregeln für Standard-Konstruktor unterliegen. Der abgeleitete Typ muss auch über einen Standardkonstruktor verfügen, und diesen Konstruktor muss mindestens so kritisch Standardkonstruktor des Basistyps sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um die Verletzung zu beheben, entfernen Sie den Typ, oder leiten Sie nicht von nicht transparenten Typ.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnungen, die von dieser Regel. Verstöße gegen diese Regel vom Anwendungscode führt in die CoreCLR ablehnt, die zum Laden des Typs mit einem <xref:System.TypeLoadException>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Kommentare



