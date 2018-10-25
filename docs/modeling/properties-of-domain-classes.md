---
title: Eigenschaften von Domänenklassen
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0192953ae88bf5665ea1f28356fb23f31113b76c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935080"
---
# <a name="properties-of-domain-classes"></a>Eigenschaften von Domänenklassen
Domänenklassen werden die Eigenschaften in der folgenden Tabelle sind. Weitere Informationen zu den Domänenklassen, finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Zugriffsmodifizierer|Die Zugriffsebene der Domänenklasse (`public` oder `internal`).|`public`|
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die von dieser Domänenklasse generiert wird.|\<Keine >|
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse für Code, der von der Domänenklasse generiert wird (`none`, `abstract` oder `sealed`).|`none`|
|Basisklasse|Wenn diese Domänenklasse abgeleitet ist, den Namen der Basisklasse.|\<Keine >|
|name|Der Name dieser Domänenklasse.|Aktuelle name|
|Namespace|Der Namespace dieser Domänenklasse.|Aktuellen namespace|
|Hinweise|Informelle Hinweise, die mit dieser Domäne verknüpft sind.|\<Keine >|
|Beschreibung|Die Beschreibung, die zum Dokumentieren der Benutzeroberflächenautomatisierungs des generierten Designers verwendet wird.|\<Keine >|
|Anzeigename|Der Name, der im generierten Designer für diese Domänenklasse angezeigt wird.|\<Keine >|
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Domänenklasse verwendet wird.|\<Keine >|

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)