---
title: Eigenschaften von Domänenbeziehungen
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3ec468ebedbe1d15ddff3527bcf0783b9831247e
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966439"
---
# <a name="properties-of-domain-relationships"></a>Eigenschaften von Domänenbeziehungen
Die Eigenschaften in der folgenden Tabelle sind mit einer domänenbeziehung verknüpft. Informationen des domänenbeziehungen finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Zugriffsmodifizierer|Die Zugriffsebene der domänenbeziehung (`public` oder `internal`).|`public`|
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die aus der domänenbeziehung generiert wird.|\<Keine >|
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) wird generiert. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, gibt an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse für Code, der aus die domänenbeziehung generiert wird (`none`, `abstract` oder `sealed`).|\<Keine >|
|Duplikate zulässt|Wenn `True`, doppelte Links die domänenbeziehung zwischen den gleichen zwei Elementen erstellt werden kann.|`False`|
|Basisbeziehungen|Wenn die domänenbeziehung abgeleitet ist, die basisbeziehung die domänenbeziehung.|\<Keine >|
|Einbetten von ist|Wenn `True`, die domänenbeziehung gibt eine einbettende Beziehung. Wenn `False`, die Beziehung ist eine verweisbeziehung.|\<Beide >|
|name|Der Name der domänenbeziehung.|Aktuelle name|
|Namespace|Der Namespace, der die domänenbeziehung zugeordnet ist.|Aktuellen namespace|
|Hinweise|Informelle Hinweise, die die domänenbeziehung zugeordnet sind.|\<Keine >|
|Beschreibung|Die Beschreibung, die wird verwendet, um Code zu dokumentieren, die in der Benutzeroberfläche des generierten Designers verwendet wird.|\<Keine >|
|Anzeigename|Der Name, der im generierten Designer für die domänenbeziehung angezeigt wird.|\<Keine >|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die domänenbeziehung verwendet wird.|\<Keine >|

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)