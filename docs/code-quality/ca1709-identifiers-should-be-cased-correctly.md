---
title: 'CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldBeCasedCorrectly
- CA1709
helpviewer_keywords:
- CA1709
- IdentifiersShouldBeCasedCorrectly
ms.assetid: f633d1a7-4ca4-40ae-b207-ec571c5fb083
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f692218cd051338a6bd4e83a07d985bb52f907e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546234"
---
# <a name="ca1709-identifiers-should-be-cased-correctly"></a>CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.

|||
|-|-|
|TypeName|IdentifiersShouldBeCasedCorrectly|
|CheckId|CA1709|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Wichtige – Wenn auf Assemblys, Namespaces, Typen, Member und Parameter ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für den generischen Parameter des Typs ausgelöst.|

## <a name="cause"></a>Ursache
 Der Name eines Bezeichners ist keine korrekte Groß-/Kleinschreibung.

 \- oder –

 Der Name eines Bezeichners enthält eine zweibuchstabige Abkürzung, und ist der zweite Buchstaben in Kleinbuchstaben.

 \- oder –

 Der Name eines Bezeichners enthält ein Akronym mindestens drei Großbuchstaben.

## <a name="rule-description"></a>Regelbeschreibung
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Diese Konsistenz reduziert die Lernkurve, die für neue Softwarebibliotheken erforderlich ist, und zudem wird das Kundenvertrauen, dass die Bibliothek von einer Person entwickelt wurde, die Erfahrung in der Entwicklung von verwaltetem Code hat.

 Gemäß der Konvention Parameternamen Camel-Case Groß-/Kleinschreibung, und einen Namespace, Typ und Elementnamen Pascal-Schreibweise zur Groß-und Kleinschreibung. In einem Namen in Kamel-Schreibweise der erste Buchstabe ist in Kleinbuchstaben, und die erste Buchstaben des verbleibenden Wörter im Namen ist groß geschrieben. Beispiele für Namen in Kamel-Schreibweise sind `packetSniffer`, `ioFile`, und `fatalErrorCode`. In einem Namen Pascal-Schreibweise verwendet der erste Buchstaben wird Groß- und die erste Buchstaben des verbleibenden Wörter im Namen ist groß geschrieben. Beispiele für Namen Pascal-Schreibweise angegeben sind `PacketSniffer`, `IOFile`, und `FatalErrorCode`.

 Diese Regel den Namen in Wörter, die basierend auf die Groß-/Kleinschreibung unterteilt und überprüft alle zwei Buchstaben bestehenden Wörter mit einer Liste der allgemeinen zwei Buchstaben bestehenden Wörter wie "In" oder "My". Wenn eine Übereinstimmung nicht gefunden wird, wird angenommen, dass das Wort ein Akronym handelt. Mit dieser Regel wird außerdem davon ausgegangen, dass es ein Akronym gefunden hat, wenn Sie den Namen entweder vier Großbuchstaben in einer Zeile oder drei Großbuchstaben in einer Zeile am Ende des Namens enthält.

 Gemäß der Konvention verwenden zwei Buchstaben bestehenden Akronyme Großbuchstaben und Akronyme der drei oder mehr Zeichen verwenden Pascal-Schreibweise zur Groß-und Kleinschreibung. Die folgenden Beispiele verwenden die Benennungskonvention: "DB", "CR", "Cpa" und "Ecma". In den folgenden Beispielen verstoßen gegen die Konvention: '-E/a', 'XML' und "DoD", und für nicht-Parameternamen, "Xp" und "cpl".

 "ID" ist, einen Sonderfall dar, die dazu führen, dass einen Verstoß gegen diese Regel. "Id" ist kein Akronym, aber es ist eine Abkürzung für "ID".

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie den Namen, damit sie die richtige Groß-/Kleinschreibung ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, diese Warnung zu unterdrücken, wenn Sie Ihre eigenen Benennungskonventionen haben oder wenn der Bezeichner, einen ordnungsgemäßen Namen, z. B. den Namen eines Unternehmens oder eine Technologie darstellt.

 Sie können auch bestimmte Begriffe, Abkürzungen und Akronyme hinzufügen, um ein benutzerdefiniertes Wörterbuch des Code-Analyse. In benutzerdefinierten Wörterbuchs angegebenen Begriffe verursacht keine Verstöße gegen diese Regel. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

## <a name="related-rules"></a>Verwandte Regeln
 [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)