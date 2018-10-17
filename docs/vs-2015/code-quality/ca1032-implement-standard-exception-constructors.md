---
title: 'CA1032: Standardausnahmekonstruktoren implementieren | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 871381e1013face4531e90b06d680d194955e3c0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193595"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032: Standardausnahmekonstruktoren implementieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ erweitert <xref:System.Exception?displayProperty=fullName> und nicht alle erforderlichen Konstruktoren deklariert.

## <a name="rule-description"></a>Regelbeschreibung
 Typen müssen die folgenden Konstruktoren implementieren:

-   Öffentliche NewException()

-   Öffentliche NewException(string)

-   Öffentliche NewException (String, Ausnahme)

-   geschützt oder privat NewException (SerializationInfo-Objekt, StreamingContext)

 Falls nicht der vollständige Satz von Konstruktoren angegeben wird, wird eine ordnungsgemäße Behandlung von Ausnahmen unter Umständen erschwert. Z. B. der Konstruktor mit der Signatur `NewException(string, Exception)` wird verwendet, um Ausnahmen zu erstellen, die von anderen Ausnahmen verursacht werden. Ohne diesen Konstruktor nicht möglich, erstellen und Auslösen von einer Instanz der benutzerdefinierten Ausnahme, die eine Ausnahme des innere (geschachtelte) enthält, ist die an, welche verwalteter Code in einem solchen Fall tun. Die ersten drei Standardausnahmekonstruktoren sind standardmäßig öffentlich. Der vierte Konstruktor ist in nicht versiegelte Klassen geschützt und im versiegelte Klassen privat. Weitere Informationen finden Sie unter [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie die fehlenden Konstruktoren, auf die Ausnahme, und stellen Sie sicher, dass sie die richtige Zugriffsebene verfügen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, wenn die Verletzung verursacht wird, eine andere Zugriffsebene für die öffentlichen Konstruktoren mit.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält einen Ausnahmetyp, der gegen diese Regel verstößt und einem Ausnahmetyp, der ordnungsgemäß implementiert ist.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]



