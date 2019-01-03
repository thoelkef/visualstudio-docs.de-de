---
title: 'CA2137: Transparente Methoden dürfen nur überprüfbare IL enthalten.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 76d628b05ae5c0b6ccb8db94a1bf2c09537fd812
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913197"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Transparente Methoden dürfen nur überprüfbare IL enthalten.

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode enthält nicht überprüfbaren Code oder gibt einen Typ nach Verweis zurück.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird für Versuche durch sicherheitstransparenten Code ausgelöst, nicht überprüfbare MSIL (Microsoft Intermediate Language) auszuführen. Die Regel enthält jedoch kein vollständiges IL-Prüfmodul und verwendet stattdessen Heuristik, um die meisten Verletzungen der MSIL-Überprüfung abzufangen.

 Um sicherzustellen, dass der Code nur überprüfbare MSIL enthält, führen Sie [Peverify.exe (PEVerify-Tool)](/dotnet/framework/tools/peverify-exe-peverify-tool) auf die Assembly. Führen Sie PEVerify mit der **/ transparent** Option aus, die die Ausgabe nur nicht überprüfbare transparente Methoden beschränkt, die einen Fehler verursachen würden. Wenn die / Option "transparent" nicht verwendet wird, überprüft PEVerify auch wichtige Methoden, die nicht überprüfbaren Code enthalten dürfen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode mit dem <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut, oder entfernen Sie die nicht überprüfbaren Code.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die Methode in diesem Beispiel wird nicht überprüfbaren Code verwendet und sollte mit markiert werden die <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]