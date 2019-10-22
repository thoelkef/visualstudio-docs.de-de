---
title: Eigenschaften von Bildformen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a89d7e5710f7a80c4e1f134ce2dfe2bd35ed5337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658145"
---
# <a name="properties-of-image-shapes"></a>Eigenschaften von Bildformen

Mithilfe von Bildformen können Sie angeben, wie Domänen Klassen in einem generierten Designer angezeigt werden. Definieren Sie eine Bildform, indem Sie die `Image`-Eigenschaft der-Klasse auf eine vordefinierte Bilddatei festlegen. Die folgenden Formate werden unterstützt:

- GIF

- JPG

- JPEG

- . bmp

- . WMF

- . EMF

- .png

Standardmäßig befinden sich Designer-Ressourcen Dateien, z. b. Bilddateien, im Ordner " **Ressourcen** " im **DSL** -Projekt.

Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

Bildformen verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|property|Beschreibung|Default|
|-|-|-|
|Füllfarbe|Die Füllfarbe dieser Form.|Weiß|
|Füllverlaufs Modus|Der Füllverlaufs Modus dieser Form.|Horizontal|
|Hat Standard Verbindungspunkte|Wenn `True`, verwendet die Form die oberen, unteren, linken und rechten Verbindungspunkte im generierten Designer.|False|
|Umriss Farbe|Die Kontur Farbe dieser Form.|Schwarz|
|Umriss Strich Stil|Der Umriss Strich Stil dieser Form (Solid, Dash, dot, DashDot, DashDotDot oder Custom).|Basis|
|Kontur Stärke|Die Gliederungs Stärke dieser Form.|0,03125|
|Textfarbe|Die Farbe, die für Text-Decorator verwendet wird, die dieser Form zugeordnet sind.|Schwarz|
|Zugriffsmodifizierer|Der Zugriffsmodifizierer der Geometrie Form (öffentlich oder intern).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der Quell Code Klasse Attribute hinzuzufügen, die aus dieser Form generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Wenn `True`, werden sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, wird ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus der Form "Image" (`none`, `abstract` oder `sealed`) generiert wird.|Keine|
|Basis Bild Form|Die Basisklasse dieser Form.|(keine)|
|-Name|Der Name dieser Form.|Aktueller Name|
|Namespace|Der Namespace, der mit dieser Form verbunden ist.|Aktueller Namespace|
|QuickInfo-Typ|Die Stelle, an der die QuickInfo definiert ist (Fixed, Variable oder None). Wenn ein fester Wert angezeigt wird, wird der Wert der `Fixed Tooltip Text`-Eigenschaft als QuickInfo verwendet. Wenn die Variable ist, wird die QuickInfo in benutzerdefiniertem Code definiert.|Keine|
|Notizen|Informelle Notizen, die dieser Form zugeordnet sind.|\<none>|
|Anfängliche Höhe|Die Anfangshöhe dieser Form in Zoll.|1|
|Anfängliche Breite|Die ursprüngliche Breite dieser Form in Zoll.|1.5|
|Verfügbar gemachte Füllfarbe als Eigenschaft<br /><br /> Offen gelegter Füllverlaufs Modus<br /><br /> Verfügbar gemachte Umriss Farbe als Eigenschaft<br /><br /> Darstellung des Gliederungs Bindestrich Stils als Eigenschaft<br /><br /> Verfügbar gemachte Gliederungs Stärke als Eigenschaft<br /><br /> Macht Textfarbe verfügbar.|Wenn `True`, kann der Benutzer die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Definition, und **Klicken Sie auf**verfügbar machen|False|
|Beschreibung|Wird verwendet, um den generierten Designer zu dokumentieren.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diese Form angezeigt wird.|\<none>|
|Fester QuickInfo-Text|Der Text, der für eine fixierte QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Element verwendet wird.|\<none>|
|Bild|Der Pfad zur Bilddatei, die für diese Form verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)