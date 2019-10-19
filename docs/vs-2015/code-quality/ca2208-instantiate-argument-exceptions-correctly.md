---
title: 'CA2208: Argument Ausnahmen ordnungsgemäß instanziieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5b5e1525d1ee706f9cd46a58c022763d2ed234bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662682"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208: Argumentausnahmen korrekt instanziieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Zu den möglichen Ursachen gehören die folgenden Situationen:

- Der standardmäßige (parameterlose) Konstruktor eines Ausnahme Typs, der ist oder von [System. ArgumentException] abgeleitet ist, wird aufgerufen (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->) auf den zugehörigen gespeicherten Wert zugreifen.

- Ein falsches Zeichen folgen Argument wird an einen parametrisierten Konstruktor eines Ausnahme Typs übergeben, der ist oder von [System. ArgumentException] abgeleitet ist. (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Regelbeschreibung
 Anstatt den Standardkonstruktor aufzurufen, rufen Sie eine der Konstruktorüberladungen auf, die eine aussagekräftigere Ausnahme Meldung bereitstellen lassen. Die Ausnahme Meldung sollte den Entwickler als Ziel haben und die Fehlerbedingung und die Vorgehensweise zur Behebung oder Vermeidung der Ausnahme eindeutig erläutern.

 Die Signaturen der einen und zwei zeichenfolgenkonstruktoren von <xref:System.ArgumentException> und der abgeleiteten Typen sind hinsichtlich der `message`-und `paramName`-Parameter nicht konsistent. Stellen Sie sicher, dass diese Konstruktoren mit den richtigen Zeichen folgen Argumenten aufgerufen werden. Die Signaturen lauten wie folgt:

 <xref:System.ArgumentException> (Zeichenfolge `message`)

 <xref:System.ArgumentException> (Zeichenfolge `message`, Zeichenfolge `paramName`)

 <xref:System.ArgumentNullException> (Zeichenfolge `paramName`)

 <xref:System.ArgumentNullException> (Zeichenfolge `paramName`, Zeichenfolge `message`)

 <xref:System.ArgumentOutOfRangeException> (Zeichenfolge `paramName`)

 <xref:System.ArgumentOutOfRangeException> (Zeichenfolge `paramName`, Zeichenfolge `message`)

 <xref:System.DuplicateWaitObjectException> (Zeichenfolge `parameterName`)

 <xref:System.DuplicateWaitObjectException> (Zeichenfolge `parameterName`, Zeichenfolge `message`)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie einen Konstruktor aufrufen, der eine Nachricht, einen Parameternamen oder beides annimmt, und sicherstellen, dass die Argumente für den Typ der aufgerufenen <xref:System.ArgumentException> richtig sind.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel nur zu unterdrücken, wenn ein parametrisierter Konstruktor mit den richtigen Zeichen folgen Argumenten aufgerufen wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Konstruktor, der eine Instanz des ArgumentNullException-Typs fälschlicherweise instanziiert.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die obige Verletzung behoben, indem die Konstruktorargumente gewechselt werden.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
