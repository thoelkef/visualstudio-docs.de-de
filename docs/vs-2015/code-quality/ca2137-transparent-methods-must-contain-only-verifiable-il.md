---
title: 'CA2137: transparente Methoden dürfen nur überprüfbare Il enthalten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6219acde1f62c946e08325f4764dc49dde461d2f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546574"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Transparente Methoden dürfen nur überprüfbare IL enthalten.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|Transparentmethodsmustbeprüfbar|
|CheckId|CA2137|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode enthält nicht überprüfbaren Code oder gibt einen Typ nach Verweis zurück.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel wird für Versuche durch sicherheitstransparenten Code ausgelöst, nicht überprüfbare MSIL (Microsoft Intermediate Language) auszuführen. Die Regel enthält jedoch kein vollständiges IL-Prüfmodul und verwendet stattdessen Heuristik, um die meisten Verletzungen der MSIL-Überprüfung abzufangen.

 Um sicherzustellen, dass Ihr Code nur überprüfbare MSIL enthält, führen Sie [Peverify.exe (Tool "Peer verify")](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) für die Assembly aus. Führen Sie "Peer verify" mit der **/transparent** -Option aus, die die Ausgabe auf nicht überprüfbare transparente Methoden beschränkt, die einen Fehler verursachen würden. Wenn die/transparent-Option nicht verwendet wird, überprüft Peer Verify auch kritische Methoden, die nicht überprüfbaren Code enthalten dürfen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut oder dem- <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, oder entfernen Sie den nicht überprüfbaren Code.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die-Methode in diesem Beispiel verwendet nicht überprüfbaren Code und sollte mit dem- <xref:System.Security.SecurityCriticalAttribute> Attribut oder dem-Attribut gekennzeichnet sein <xref:System.Security.SecuritySafeCriticalAttribute> .

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
