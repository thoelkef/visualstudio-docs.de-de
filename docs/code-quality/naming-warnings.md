---
title: Benennungswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6d1e40b809f27292f2a808458584837913d881f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587302"
---
# <a name="naming-warnings"></a>Benennungswarnungen

Benennungs Warnungen unterstützen die Einhaltung der Benennungs Konventionen der .net-Entwurfs Richtlinien.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1700: Enumerationswerte nicht mit "Reserviert" benennen.](../code-quality/ca1700.md)|Bei dieser Regel wird vorausgesetzt, dass Enumerationsmember mit einem Namen, der "reserved" enthält, derzeit nicht verwendet werden, sondern Platzhalter sind, die in einer künftigen Version umbenannt oder entfernt werden sollen. Das Umbenennen oder Entfernen eines Members ist eine unterbrechende Änderung.|
|[CA1713: Ereignisse sollten kein Before- oder After-Präfix aufweisen.](../code-quality/ca1713.md)|Der Name eines Ereignisses beginnt mit "Before" oder "After". Um verwandte Ereignisse zu benennen, die in einer bestimmten Reihenfolge ausgelöst werden, verwenden Sie die Gegenwarts- oder Vergangenheitsform, um ihre relative Position in der Aktionsfolge anzugeben.|
|[CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1714.md)|Eine öffentliche Enumeration weist das System. FlagsAttribute-Attribut auf, und der Name endet nicht mit "s". Typen, die mit FlagsAttribute gekennzeichnet sind, haben Namen, die den Plural aufweisen, da das Attribut angibt, dass mehr als ein Wert angegeben werden kann.|
|[CA1704: Bezeichner sollten korrekt geschrieben werden.](../code-quality/ca1704.md)|Der Name eines extern sichtbaren Bezeichners enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.|
|[CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708.md)|Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß-/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß- und Kleinschreibung unterscheiden müssen.|
|[CA1715: Bezeichner sollten ein korrektes Präfix aufweisen.](../code-quality/ca1715.md)|Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit einem Großbuchstaben "I".  Der Name eines generischen Typparameters für einen extern sichtbaren Typ oder eine extern sichtbare Methode beginnt nicht mit dem Großbuchstaben "T".|
|[CA1720: Bezeichner dürfen keine Typnamen enthalten.](../code-quality/ca1720.md)|Der Name eines Parameters in einem extern sichtbaren Member enthält einen Datentypnamen, oder der Name eines extern sichtbaren Members enthält einen sprachspezifischen Datentypnamen.|
|[CA1722: Bezeichner sollten kein falsches Präfix aufweisen.](../code-quality/ca1722.md)|Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen.|
|[CA1711: Bezeichner sollten kein falsches Suffix aufweisen.](../code-quality/ca1711.md)|Nur die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. Typen implementieren, die von diesen Typen abgeleitet werden, sollten stets mit bestimmten reservierten Suffixen enden. Für andere Typnamen sollten diese reservierten Suffixe nicht verwendet werden.|
|[CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1717.md)|Gemäß den Benennungskonventionen gibt ein Pluralname für eine Enumeration an, dass für die Enumeration mehrere Werte gleichzeitig angegeben werden können.|
|[CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen.](../code-quality/ca1725.md)|Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen. Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt.|
|[CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.](../code-quality/ca1719.md)|Ein Parameter Name sollte die Bedeutung eines Parameters vermitteln, und ein Elementname sollte die Bedeutung eines Members übermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.|
|[CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1701.md)|Jedes Wort in der Ressourcen Zeichenfolge wird in Token aufgeteilt, die auf der Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft-Bibliothek überprüft. Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß.|
|[CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden.](../code-quality/ca1703.md)|Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.|
|[CA1724: Typnamen sollten nicht mit Namespaces übereinstimmen.](../code-quality/ca1724.md)|Typnamen sollten nicht mit den Namen von .NET-Namespaces identisch sein. Durch einen Verstoß gegen diese Regel kann die Benutzerfreundlichkeit der Bibliothek reduziert werden.|
|[CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707.md)|Bezeichnernamen dürfen keinen Unterstrich (_) enthalten. Namespaces, Typen, Member und Parameter werden von dieser Regel überprüft.|
|[CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden übereinstimmen.](../code-quality/ca1721.md)|Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und stimmt in anderer Hinsicht mit dem Namen einer öffentlichen oder geschützten Eigenschaft überein. "Get"-Methoden und -Eigenschaften sollten Namen aufweisen, die ihre Funktionen deutlich erkennbar machen.|
|[CA1716: Bezeichner sollten nicht mit Schlüsselwörtern übereinstimmen.](../code-quality/ca1716.md)|Ein Namespacename oder ein Typname stimmt mit einem reservierten Schlüsselwort in einer Programmiersprache überein. Bezeichner für Namespaces und Typen dürfen nicht mit Schlüsselwörtern übereinstimmen, die in Programmiersprachen für die Common Language Runtime definiert sind.|
|[CA1726: Bevorzugte Begriffe verwenden.](../code-quality/ca1726.md)|Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Der Name kann auch den Begriff "Flag" oder "Flags" enthalten.|
|[CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1709.md)|Gemäß der Konvention verwenden Parameternamen die Kamel-Schreibweise, und Namespace-, Typ-und Elementnamen verwenden Pascal-Schreibweise.|
|[CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1702.md)|Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß-/Kleinschreibung.|
|[CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden.](../code-quality/ca1712.md)|Namen von Enumerationsmembern haben nicht den Typnamen als Präfix, da von den Entwicklungs Tools Typinformationen erwartet werden.|
|[CA1710: Bezeichner sollten ein richtiges Suffix aufweisen.](../code-quality/ca1710.md)|Gemäß der Konvention verfügen die Namen von Typen, die bestimmte Basis Typen erweitern oder bestimmte Schnittstellen oder Typen implementieren, die von diesen Typen abgeleitet sind, über ein Suffix, das dem Basistyp oder der Schnittstelle zugeordnet ist.|
