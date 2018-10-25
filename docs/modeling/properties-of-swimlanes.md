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
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e316caa9ededbb7db40490fcbcc10ec4f760497d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903750"
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
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Codeklasse hinzuzufügen, die von dieser Swimlane generiert wird.|\<Keine >|
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse in der Code ein, das mit der Swimlane generiert (`none`, `abstract` oder `sealed`).|Keine|
|Basisswimlane|Die Basisklasse dieser swimlane.|(keine)|
|name|Der Name dieser swimlane.|Aktuelle name|
|Namespace|Der Namespace, der dieser Swimlane zugeordnet ist.|Aktuellen namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert ist (`fixed`, `variable`, oder `none`). Wenn `fixed`, klicken Sie dann den Wert, der die `Fixed Tooltip Text` Eigenschaft verwendet wird; Wenn `variable`, und klicken Sie dann die QuickInfo in benutzerdefiniertem Code definiert ist.|\<Keine >|
|Hinweise|Informelle Hinweise, die dieser Swimlane zugeordnet sind.|\<Keine >|
|Ausrichtung|Horizontale oder vertikale Ausrichtung.|Vertikal|
|Die ursprüngliche Höhe|Die ursprüngliche Höhe dieser Swimlane in Zoll. Gilt nur für horizontale Swimlanes.|0|
|Die ursprüngliche Breite|Die ursprüngliche Breite dieser swimlane in Zoll. Gilt nur für vertikale Swimlanes.|0|
|Stellt Text Color|Wenn `True`, der Benutzer kann die Farbe einer swimlane im generierten Designer festlegen. Um dies festzulegen, mit der rechten Maustaste der swimlaneform, und klicken Sie auf **verfügbare hinzufügen**.|False|
|Beschreibung|Dokumentieren des generierten Designers verwendet.|\<Keine >|
|Anzeigename|Der Name, der im generierten Designer zum Verweisen auf diese Klasse des verantwortlichkeitsbereichs angezeigt wird.|\<Keine >|
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<Keine >|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieser Swimlane verwendet wird.|\<Keine >|

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)