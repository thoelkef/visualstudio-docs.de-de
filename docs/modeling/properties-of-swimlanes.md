---
title: Eigenschaften von Verantwortlichkeitsbereichen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5180581b0a0934c049d9c4ea199fa3396a1d1237
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658119"
---
# <a name="properties-of-swimlanes"></a>Eigenschaften von Verantwortlichkeitsbereichen
Sie können einem Diagramm Verantwortlichkeits Bereiche hinzufügen. Swimlanes unterteilen ein Diagramm in vertikale oder horizontale Bereiche. Sie können andere Formen definieren, die in Swimlanes angezeigt werden. Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Swimlanes verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|property|Beschreibung|Default|
|-|-|-|
|Füllfarbe für Text|Die Füllfarbe für den Text der swimlane.|Weiß|
|Füllfarbe für Header|Die Füllfarbe für den Header der swimlane.|DarkGray|
|Trennzeichen Farbe|Die Farbe der Trennlinie.|Hellgrau|
|Trennlinien Stil|Der Stil der Trennlinie (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot` oder `Custom`).|`Dash`|
|Trennzeichen Stärke|Die Stärke der Trennlinie in Zoll.|0,03125|
|Textfarbe|Die Farbe, die für Text-Decorator verwendet wird, die dieser Swimlane zugeordnet sind.|Schwarz|
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse (`public` oder `internal`).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der Code Klasse Attribute hinzuzufügen, die von dieser Swimlane generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Wenn `True`, werden sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, wird ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus der Swimlane generiert wird (`none`, `abstract` oder `sealed`).|Keine|
|Grund Verantwortlichkeits Bereich|Die Basisklasse dieser swimlane.|(keine)|
|-Name|Der Name dieser swimlane.|Aktueller Name|
|Namespace|Der Namespace, der mit dieser Swimlane verbunden ist.|Aktueller Namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert wird (`fixed`, `variable` oder `none`). Wenn `fixed`, wird der Wert der `Fixed Tooltip Text`-Eigenschaft verwendet. Wenn `variable`, wird die QuickInfo in benutzerdefiniertem Code definiert.|\<none>|
|Notizen|Informelle Notizen, die dieser Swimlane zugeordnet sind.|\<none>|
|Ausrichtung|Horizontale oder vertikale Ausrichtung.|Vertikal|
|Anfängliche Höhe|Die Anfangshöhe dieser Swimlane in Zoll. Gilt nur für horizontale Swimlanes.|0|
|Anfängliche Breite|Die ursprüngliche Breite dieser Swimlane in Zoll. Gilt nur für vertikale Swimlanes.|0|
|Macht Textfarbe verfügbar.|Wenn `True`, kann der Benutzer die Farbe einer Swimlane im generierten Designer festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Verantwortlichkeits Bereich und **Klicken auf verfügbar machen.**|False|
|Beschreibung|Wird verwendet, um den generierten Designer zu dokumentieren.|\<none>|
|Anzeigename|Der Name, der im generierten Designer angezeigt wird, um auf diese Swimlane-Klasse zu verweisen.|\<none>|
|Fester QuickInfo-Text|Der Text, der für eine fixierte QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Swimlane verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)