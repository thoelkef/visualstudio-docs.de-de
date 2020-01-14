---
title: 'CA1709: Bezeichner müssen ordnungsgemäß geschrieben werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c4da0414c9923a8ed7bb01456f38000433641522
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919232"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1709: Bezeichner sollten korrekt geschrieben werden](/visualstudio/code-quality/ca1709-identifiers-should-be-cased-correctly).

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechen: Wenn Assemblys, Namespaces, Typen, Member und Parameter ausgelöst werden.<br /><br /> Nicht unterbrechend: Wenn Sie für generische Typparameter ausgelöst werden.|

## <a name="cause"></a>Ursache
 Der Name eines Bezeichners ist nicht ordnungsgemäß geschrieben.

 \- oder -

 Der Name eines Bezeichners enthält einen aus zwei Buchstaben bestehenden Akronym und den zweiten Buchstaben in Kleinbuchstaben.

 \- oder -

 Der Name eines Bezeichners enthält ein Akronym von drei oder mehr Großbuchstaben.

## <a name="rule-description"></a>Regelbeschreibung
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

 Gemäß der Konvention verwenden Parameternamen die Kamel Schreibweise. Namespace-, Typ-und Elementnamen verwenden Pascal-Schreibweise. Bei einem Kamel Namen ist der erste Buchstabe klein geschrieben, und der erste Buchstabe der restlichen Wörter im Namen ist in Großbuchstaben. Beispiele für die Namen von Kamel Namen sind "Packetsniffer", "IOFile" und "FatalErrorCode". In einem Namen mit Pascal-Schreibweise ist der erste Buchstabe Großbuchstaben, und der erste Buchstabe der restlichen Wörter im Namen ist in Großbuchstaben. Beispiele für Namen von Pascal-Bezeichnernamen sind "Packetsniffer", "IOFile" und "FatalErrorCode".

 Diese Regel teilt den Namen auf der Grundlage der Groß-und Kleinschreibung in Wörter auf und überprüft alle zwei Buchstaben mit einer Liste von gängigen zwei buchstabwörtern, wie z. b. "in" oder "My". Wenn keine Entsprechung gefunden wird, wird angenommen, dass es sich bei dem Wort um ein Akronym handelt. Außerdem geht diese Regel davon aus, dass Sie ein Akronym gefunden hat, wenn der Name entweder vier Großbuchstaben in einer Zeile oder drei Großbuchstaben in einer Zeile am Ende des Namens enthält.

 Gemäß der Konvention verwenden zwei Buchstaben Akronyme alle Großbuchstaben, und für Akronyme von drei oder mehr Zeichen wird die Pascal-Schreibweise verwendet. In den folgenden Beispielen wird diese Benennungs Konvention verwendet: ' DB ', ' CR ', ' CPA ' und ' ECMA '. Die folgenden Beispiele verstoßen gegen die Konvention: "IO", "XML" und "DoD", und für nicht Parameternamen "XP" und "cpl".

 "ID" ist ein Sonderzeichen, um einen Verstoß gegen diese Regel zu verursachen. ' ID ' ist kein Akronym, aber ist eine Abkürzung für ' Identification '.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie den Namen so, dass er richtig geschrieben ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, diese Warnung zu unterdrücken, wenn Sie Ihre eigenen Benennungs Konventionen haben, oder wenn der Bezeichner einen richtigen Namen darstellt, z. b. den Namen eines Unternehmens oder einer Technologie.

 Sie können einem benutzerdefinierten Code Analyse Wörterbuch auch bestimmte Begriffe, Abkürzungen und Akronyme hinzufügen. Im benutzerdefinierten Wörterbuch angegebene Begriffe verursachen keine Verstöße gegen diese Regel. Weitere Informationen finden Sie unter Gewusst [wie: Anpassen des Code Analyse Wörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md) .

## <a name="related-rules"></a>Verwandte Regeln
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
