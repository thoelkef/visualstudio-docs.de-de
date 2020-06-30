---
title: 'CA1032: Standardausnahmekonstruktoren implementieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 61b0157200ddff4cb8335118b30832a0c8950f65
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542284"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standardausnahmekonstruktoren implementieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ erweitert <xref:System.Exception?displayProperty=fullName> und deklariert nicht alle erforderlichen Konstruktoren.

## <a name="rule-description"></a>Beschreibung der Regel
 Ausnahme Typen müssen die folgenden Konstruktoren implementieren:

- Public "netwexception ()"

- Public "netwexception" (Zeichenfolge)

- Public "netwexception" (String, Exception)

- Protected or private, "netwexception" (SerializationInfo, StreamingContext)

  Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert. Beispielsweise wird der Konstruktor mit der Signatur `NewException(string, Exception)` verwendet, um Ausnahmen zu erstellen, die durch andere Ausnahmen verursacht werden. Ohne diesen Konstruktor können Sie keine Instanz Ihrer benutzerdefinierten Ausnahme erstellen und auslösen, die eine innere (geschachtelte) Ausnahme enthält. Dies ist der Zweck, den verwalteter Code in einer solchen Situation ausführen sollte. Die ersten drei Ausnahmekonstruktoren sind gemäß Konvention öffentlich. Der vierte Konstruktor ist in nicht versiegelten Klassen und privat in versiegelten Klassen geschützt. Weitere Informationen finden Sie unter [CA2229: Implementieren von Serialisierungskonstruktoren](../code-quality/ca2229-implement-serialization-constructors.md) .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Ausnahme die fehlenden Konstruktoren hinzu, und stellen Sie sicher, dass Sie über die richtige Barrierefreiheit verfügen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Verletzung durch die Verwendung einer anderen Zugriffsebene für die öffentlichen Konstruktoren verursacht wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält einen Ausnahmetyp, der gegen diese Regel verstößt, und einen Ausnahmetyp, der ordnungsgemäß implementiert ist.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
