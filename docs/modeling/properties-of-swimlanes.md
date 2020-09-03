---
title: Eigenschaften von Verantwortlichkeitsbereichen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cceeacab44f17eb30184c90f1128b8d2c3528bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115366"
---
# <a name="properties-of-swimlanes"></a>Eigenschaften von Verantwortlichkeitsbereichen
Sie können einem Diagramm Verantwortlichkeits Bereiche hinzufügen. Swimlanes unterteilen ein Diagramm in vertikale oder horizontale Bereiche. Sie können andere Formen definieren, die in Swimlanes angezeigt werden. Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Swimlanes verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Füllfarbe für Text|Die Füllfarbe für den Text der swimlane.|White|
|Füllfarbe für Header|Die Füllfarbe für den Header der swimlane.|DarkGray|
|Trennzeichen Farbe|Die Farbe der Trennlinie.|Hellgrau|
|Trennlinien Stil|Der Stil der Trennlinie ( `Solid` , `Dash` , `Dot` , `DashDot` , `DashDotDot` oder `Custom` ).|`Dash`|
|Trennzeichen Stärke|Die Stärke der Trennlinie in Zoll.|0,03125|
|Textfarbe|Die Farbe, die für Text-Decorator verwendet wird, die dieser Swimlane zugeordnet sind.|Schwarz|
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse ( `public` oder `internal` ).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der Code Klasse Attribute hinzuzufügen, die von dieser Swimlane generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Gibt `True` an, dass sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert werden. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Gibt `True` an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus der Swimlane ( `none` `abstract` oder) generiert wird `sealed` .|none|
|Grund Verantwortlichkeits Bereich|Die Basisklasse dieser swimlane.|(none)|
|Name|Der Name dieser swimlane.|Aktueller Name|
|Namespace|Der Namespace, der mit dieser Swimlane verbunden ist.|Aktueller Namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert wird ( `fixed` , `variable` oder `none` ). Wenn `fixed` , dann wird der Wert der- `Fixed Tooltip Text` Eigenschaft verwendet. Wenn `variable` , dann wird die QuickInfo in benutzerdefiniertem Code definiert.|\<none>|
|Notizen|Informelle Notizen, die dieser Swimlane zugeordnet sind.|\<none>|
|Ausrichtung|Horizontale oder vertikale Ausrichtung.|Vertical|
|Anfängliche Höhe|Die Anfangshöhe dieser Swimlane in Zoll. Gilt nur für horizontale Swimlanes.|0|
|Anfängliche Breite|Die ursprüngliche Breite dieser Swimlane in Zoll. Gilt nur für vertikale Swimlanes.|0|
|Macht Textfarbe verfügbar.|Wenn `True` der Wert ist, kann der Benutzer die Farbe einer Swimlane im generierten Designer festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Verantwortlichkeits Bereich und **Klicken auf verfügbar machen.**|False|
|Beschreibung|Wird verwendet, um den generierten Designer zu dokumentieren.|\<none>|
|Anzeigename|Der Name, der im generierten Designer angezeigt wird, um auf diese Swimlane-Klasse zu verweisen.|\<none>|
|Fester QuickInfo-Text|Der Text, der für eine fixierte QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Swimlane verwendet wird.|\<none>|

## <a name="see-also"></a>Weitere Informationen

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
