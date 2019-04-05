---
title: Benennungswarnungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a18e958732094bd445de84d0095b688f2103a67c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960559"
---
# <a name="naming-warnings"></a>Benennungswarnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Benennungswarnungen Einhaltung der Namenskonventionen der Unterstützung der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Entwurfsrichtlinien.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen. Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung.|  
|[CA1713: Ereignisse sollten kein Before- oder after-Präfix aufweisen.](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Der Name eines Ereignisses beginnt mit "Before" oder "After". Um verwandte Ereignisse zu benennen, die in einer bestimmten Reihenfolge ausgelöst werden, verwenden Sie die Gegenwarts- oder Vergangenheitsform, um ihre relative Position in der Aktionsfolge anzugeben.|  
|[CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Eine öffentliche Enumeration verfügt über das System.FlagsAttribute-Attribut, und der Name endet nicht in "s". Mit FlagsAttribute markierten Typen haben Namen, die in der Pluralform vorliegen, da das Attribut gibt an, dass mehr als ein Wert angegeben werden kann.|  
|[CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Der Name eines extern sichtbaren Bezeichners enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.|  
|[CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß-/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß- und Kleinschreibung unterscheiden müssen.|  
|[CA1715: Bezeichner sollten ein korrektes Präfix aufweisen](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit einem Großbuchstaben "I".  Der Name der einen generischen Parameter für einen extern sichtbaren Typ oder Methode beginnt nicht mit dem Großbuchstaben "T".|  
|[CA1720: Bezeichner dürfen keine Typnamen enthalten.](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen, oder der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen.|  
|[CA1722: Bezeichner sollten kein falsches Präfix aufweisen.](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen.|  
|[CA1711: Bezeichner sollten kein falsches Suffix aufweisen.](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Nur die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. Typen implementieren, die von diesen Typen abgeleitet werden, sollten stets mit bestimmten reservierten Suffixen enden. Für andere Typnamen sollten diese reservierten Suffixe nicht verwendet werden.|  
|[CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Gemäß den Benennungskonventionen gibt ein Pluralname für eine Enumeration an, dass für die Enumeration mehrere Werte gleichzeitig angegeben werden können.|  
|[CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen. Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt.|  
|[CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.|  
|[CA1701: Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Jedes Wort in der Ressourcenzeichenfolge wird in einzelne Token unterteilt, die auf die Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft-Bibliothek überprüft. Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß.|  
|[CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.|  
|[CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen.](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Typnamen dürfen nicht mit den Namen von in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Klassenbibliothek definierten Namespaces übereinstimmen. Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek reduzieren.|  
|[CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Bezeichnernamen dürfen keinen Unterstrich (_) enthalten. Namespaces, Typen, Member und Parameter werden von dieser Regel überprüft.|  
|[CA1721: Eigenschaftennamen sollten nicht mit dem Get-Methoden übereinstimmen.](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und stimmt in anderer Hinsicht mit dem Namen einer öffentlichen oder geschützten Eigenschaft überein. "Get"-Methoden und -Eigenschaften sollten Namen aufweisen, die ihre Funktionen deutlich erkennbar machen.|  
|[CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Ein Namespacename oder ein Typname stimmt mit einem reservierten Schlüsselwort in einer Programmiersprache überein. Bezeichner für Namespaces und Typen dürfen nicht mit Schlüsselwörtern übereinstimmen, die in Programmiersprachen für die Common Language Runtime definiert sind.|  
|[CA1726: Bevorzugte Begriffe verwenden](../code-quality/ca1726-use-preferred-terms.md)|Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Der Name kann auch den Begriff "Flag" oder "Flags" enthalten.|  
|[CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Gemäß der Konvention Parameternamen Camel-Case Groß-/Kleinschreibung, und einen Namespace, Typ und Elementnamen Pascal-Schreibweise zur Groß-und Kleinschreibung.|  
|[CA1702: Bei zusammengesetzten Begriffen sollte beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß-/Kleinschreibung.|  
|[CA1712: Führen Sie keine Präfixe für Enumerationswerte mit Typnamen](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Namen von Enumerationsmembern werden der Typname nicht vorangestellt werden, weil Typinformationen von Entwicklungstools bereitgestellt werden soll.|  
|[CA1710: Bezeichner sollten ein richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Gemäß der Konvention, die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen implementieren, bzw. von diesen Typen abgeleitete Typen, müssen Sie ein Suffix, das die Basisklasse oder Schnittstelle zugeordnet ist.|
