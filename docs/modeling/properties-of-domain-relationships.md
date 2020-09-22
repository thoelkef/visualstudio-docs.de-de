---
title: Eigenschaften von Domänenbeziehungen
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e432e9738009c84b6930b0363ae4048c925d0a6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810001"
---
# <a name="properties-of-domain-relationships"></a>Eigenschaften von Domänenbeziehungen
Die Eigenschaften in der folgenden Tabelle sind einer Domänen Beziehung zugeordnet. Weitere Informationen zu Domänen Beziehungen finden Sie Untergrund Legendes zu [Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Zugriffsmodifizierer|Die Zugriffsebene der Domänen Beziehung ( `public` oder `internal` ).|`public`|
|Benutzerdefinierte Attribute|Wird verwendet, um der Quell Code Klasse Attribute hinzuzufügen, die aus der Domänen Beziehung generiert werden.|\<none>|
|Generiert doppelte abgeleitete|`True`Gibt an, dass sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert werden. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Hat benutzerdefinierten Konstruktor|`True`Gibt an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus der Domänen Beziehung ( `none` oder) generiert wird `abstract` `sealed` .|\<none>|
|Lässt Duplikate zu|Wenn `True` , werden möglicherweise doppelte Verknüpfungen der Domänen Beziehung zwischen den gleichen zwei Elementen erstellt.|`False`|
|Basis Beziehungen|Wenn die Domänen Beziehung abgeleitet ist, die Basis Beziehung der Domänen Beziehung.|\<none>|
|Ist Einbettungen|`True`Gibt an, dass die Domänen Beziehung eine Embedding Relationship ist. `False`Gibt an, dass die Beziehung eine Verweis Beziehung ist.|\<both>|
|name|Der Name der Domänen Beziehung.|Aktueller Name|
|Namespace|Der Namespace, der der Domänen Beziehung zugeordnet ist.|Aktueller Namespace|
|Hinweise|Informelle Hinweise, die mit der Domänen Beziehung verknüpft sind.|\<none>|
|Beschreibung|Die Beschreibung, die verwendet wird, um Code zu dokumentieren, und wird in der Benutzeroberfläche des generierten Designers verwendet.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für die Domänen Beziehung angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die Domänen Beziehung verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))