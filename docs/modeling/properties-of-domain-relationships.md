---
title: Eigenschaften von Domänenbeziehungen
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26de877643e25413168d074d85a2aeab0794adc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658190"
---
# <a name="properties-of-domain-relationships"></a>Eigenschaften von Domänenbeziehungen
Die Eigenschaften in der folgenden Tabelle sind einer Domänen Beziehung zugeordnet. Weitere Informationen zu Domänen Beziehungen finden Sie Untergrund Legendes zu [Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|property|Beschreibung|Default|
|-|-|-|
|Zugriffsmodifizierer|Die Zugriffsebene der Domänen Beziehung (`public` oder `internal`).|`public`|
|Benutzerdefinierte Attribute|Wird verwendet, um der Quell Code Klasse Attribute hinzuzufügen, die aus der Domänen Beziehung generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Wenn `True`, wird sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, gibt an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus der Domänen Beziehung (`none`, `abstract` oder `sealed`) generiert wird.|\<none>|
|Lässt Duplikate zu|Wenn `True`, können zwischen denselben beiden Elementen doppelte Verknüpfungen der Domänen Beziehung erstellt werden.|`False`|
|Basis Beziehungen|Wenn die Domänen Beziehung abgeleitet ist, die Basis Beziehung der Domänen Beziehung.|\<none>|
|Ist Einbettungen|Wenn `True`, ist die Domänen Beziehung ein Embedding Relationship. Wenn `False`, ist die Beziehung eine Verweis Beziehung.|\<both >|
|-Name|Der Name der Domänen Beziehung.|Aktueller Name|
|Namespace|Der Namespace, der der Domänen Beziehung zugeordnet ist.|Aktueller Namespace|
|Notizen|Informelle Hinweise, die mit der Domänen Beziehung verknüpft sind.|\<none>|
|Beschreibung|Die Beschreibung, die verwendet wird, um Code zu dokumentieren, und wird in der Benutzeroberfläche des generierten Designers verwendet.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für die Domänen Beziehung angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die Domänen Beziehung verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)