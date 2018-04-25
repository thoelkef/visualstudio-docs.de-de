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
ms.technology: vs-ide-modeling
ms.openlocfilehash: 32943d7e40f7ce1a86ab2236862404686a4d922f
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-domain-relationships"></a>Eigenschaften von Domänenbeziehungen
Die Eigenschaften in der folgenden Tabelle sind die zwischen einer Domäne zugeordnet. Informationen zu domänenbeziehungen finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Eigenschaft|Beschreibung|Standard|
|--------------|-----------------|-------------|
|Zugriffsmodifizierer|Die Zugriffsebene der domänenbeziehung (`public` oder `internal`).|`public`|
|Benutzerdefinierte Attribute|Verwendet, um den Code Quellklasse Attribute hinzuzufügen, die aus der domänenbeziehung generiert wird.|\<keine >|
|Doppelter generiert abgeleitet|Wenn `True`, eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung außer Kraft) wird generiert. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Verfügt über benutzerdefinierte-Konstruktor|Wenn `True`, gibt an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Inheritance Modifier|Beschreibt die Art der Vererbung von der Quellklasse für Code, der aus der domänenbeziehung generiert wird (`none`, `abstract` oder `sealed`).|\<keine >|
|Duplikate zulässt|Wenn `True`, doppelte Links von der domänenbeziehung zwischen denselben zwei Elementen erstellt werden kann.|`False`|
|Basis-Beziehungen|Wenn die domänenbeziehung abgeleitet ist, die grundlegende Beziehung der domänenbeziehung.|\<keine >|
|Einbetten von ist|Wenn `True`, die zwischen der Domäne ist ein Einbetten von Beziehung. Wenn `False`, die Beziehung ist eine verweisbeziehung.|\<Beide >|
|Name|Der Name der domänenbeziehung.|Aktuelle name|
|Namespace|Der Namespace, der die domänenbeziehung zugeordnet ist.|Aktuellen namespace|
|Notizen|Informelle Hinweise, die mit der domänenbeziehung verknüpft sind.|\<keine >|
|Beschreibung|Die Beschreibung, die wird verwendet, um Code zu dokumentieren und in der Benutzeroberfläche des Designers generierten verwendet.|\<keine >|
|Anzeigename|Der Name, generierten für im Designer die domänenbeziehung angezeigt wird.|\<keine >|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die domänenbeziehung verwendet wird.|\<keine >|

## <a name="see-also"></a>Siehe auch

- [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)