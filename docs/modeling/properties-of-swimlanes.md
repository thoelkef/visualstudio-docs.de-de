---
title: Eigenschaften von Verantwortlichkeitsbereichen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab2e10eed7452bf58390513bed68fac3f4c9a0f6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823904"
---
# <a name="properties-of-swimlanes"></a>Eigenschaften von Verantwortlichkeitsbereichen
Sie können ein Diagramm Verantwortlichkeitsbereiche hinzufügen. Verantwortlichkeitsbereiche teilen ein Diagramms in vertikale oder horizontale Bereiche. Sie können andere Formen, die innerhalb von Verantwortlichkeitsbereichen angezeigt werden, definieren. Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Verantwortlichkeitsbereiche haben Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Text-Füllfarbe|Die Füllfarbe für den Text der Swimlane.|Weiß|
|Header-Füllfarbe|Die Füllfarbe für den Header der Swimlane.|DarkGray|
|Trennzeichenfarbe|Die Farbe der Trennlinie.|LightGray|
|Linienart Trennzeichen|Der Stil der Trennlinie (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, oder `Custom`).|`Dash`|
|Trennzeichen Stärke|Die Breite der Trennlinie in Zoll.|0.03125|
|Textfarbe|Die Farbe, die für Text-Decorators verwendet wird, die dieser Swimlane zugeordnet sind.|Schwarz|
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse (`public` oder `internal`).|Public|
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Codeklasse hinzuzufügen, die von dieser Swimlane generiert wird.|\<none>|
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse in der Code ein, das mit der Swimlane generiert (`none`, `abstract` oder `sealed`).|none|
|Basisswimlane|Die Basisklasse dieser swimlane.|(keine)|
|Name|Der Name dieser swimlane.|Aktuelle name|
|Namespace|Der Namespace, der dieser Swimlane zugeordnet ist.|Aktuellen namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert ist (`fixed`, `variable`, oder `none`). Wenn `fixed`, klicken Sie dann den Wert, der die `Fixed Tooltip Text` Eigenschaft verwendet wird; Wenn `variable`, und klicken Sie dann die QuickInfo in benutzerdefiniertem Code definiert ist.|\<none>|
|Hinweise|Informelle Hinweise, die dieser Swimlane zugeordnet sind.|\<none>|
|Ausrichtung|Horizontale oder vertikale Ausrichtung.|Vertikal|
|Die ursprüngliche Höhe|Die ursprüngliche Höhe dieser Swimlane in Zoll. Gilt nur für horizontale Swimlanes.|0|
|Die ursprüngliche Breite|Die ursprüngliche Breite dieser swimlane in Zoll. Gilt nur für vertikale Swimlanes.|0|
|Stellt Text Color|Wenn `True`, der Benutzer kann die Farbe einer swimlane im generierten Designer festlegen. Um dies festzulegen, mit der rechten Maustaste der swimlaneform, und klicken Sie auf **verfügbare hinzufügen**.|False|
|Beschreibung|Dokumentieren des generierten Designers verwendet.|\<none>|
|Anzeigename|Der Name, der im generierten Designer zum Verweisen auf diese Klasse des verantwortlichkeitsbereichs angezeigt wird.|\<none>|
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieser Swimlane verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)