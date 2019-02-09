---
title: Eigenschaften von Domänenbeziehungen
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2693994c9ead711f3bb536d0e37f485bc00047b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938175"
---
# <a name="properties-of-domain-relationships"></a>Eigenschaften von Domänenbeziehungen
Die Eigenschaften in der folgenden Tabelle sind mit einer domänenbeziehung verknüpft. Informationen des domänenbeziehungen finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Zugriffsmodifizierer|Die Zugriffsebene der domänenbeziehung (`public` oder `internal`).|`public`|
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die aus der domänenbeziehung generiert wird.|\<none>|
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) wird generiert. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, gibt an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse für Code, der aus die domänenbeziehung generiert wird (`none`, `abstract` oder `sealed`).|\<none>|
|Duplikate zulässt|Wenn `True`, doppelte Links die domänenbeziehung zwischen den gleichen zwei Elementen erstellt werden kann.|`False`|
|Basisbeziehungen|Wenn die domänenbeziehung abgeleitet ist, die basisbeziehung die domänenbeziehung.|\<none>|
|Einbetten von ist|Wenn `True`, die domänenbeziehung gibt eine einbettende Beziehung. Wenn `False`, die Beziehung ist eine verweisbeziehung.|\<both>|
|name|Der Name der domänenbeziehung.|Aktuelle name|
|Namespace|Der Namespace, der die domänenbeziehung zugeordnet ist.|Aktuellen namespace|
|Hinweise|Informelle Hinweise, die die domänenbeziehung zugeordnet sind.|\<none>|
|Beschreibung|Die Beschreibung, die wird verwendet, um Code zu dokumentieren, die in der Benutzeroberfläche des generierten Designers verwendet wird.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für die domänenbeziehung angezeigt wird.|\<none>|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die domänenbeziehung verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)