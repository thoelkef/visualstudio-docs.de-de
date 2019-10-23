---
title: Eigenschaften von Depotformen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ad53866c1930edb01ccd163131ce5e23644929c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747511"
---
# <a name="properties-of-compartment-shapes"></a>Eigenschaften von Depotformen
Depot Formen sind eine der Formen, die Sie verwenden können, um eine Domänen Klasse in einer domänenspezifischen Sprache anzuzeigen. Die Depots können erweitert und reduziert werden.

 Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Depot Formen verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|property|Beschreibung|Default|
|-|-|-|
|Standardmäßiges Erweitern des Reduzierungs Zustands|Wenn `Expanded`, werden die Depots bei der Erstellung angezeigt. Wenn `Collapsed`, ist dies nicht der Fall.|Erweitert|
|Füllfarbe|Die Füllfarbe dieser Form.|Weiß|
|Füllverlaufs Modus|Der Füllverlaufs Modus dieser Form.|Horizontal|
|Et|Die Geometrie dieser Form (Rechteck oder abgerundetes Rechteck).|Rechteck|
|Hat Standard Verbindungspunkte|Wenn `True`, verwendet die Form die oberen, unteren, linken und rechten Verbindungspunkte im generierten Designer.|False|
|Ist ein einfach Header sichtbar.|Wenn `False`, und die Form verfügt über ein einzelnes Depot, ist der Header des Depots nicht sichtbar.|True|
|Umriss Farbe|Die Kontur Farbe dieser Form.|Schwarz|
|Umriss Strich Stil|Der Umriss Strich Stil dieser Form (Solid, Dash, dot, DashDot, DashDotDot, Custom).|Basis|
|Kontur Stärke|Die Gliederungs Stärke dieser Form.|0,03125|
|Textfarbe|Die Farbe, die für Text-Decorator verwendet wird, die dieser Form zugeordnet sind.|Schwarz|
|Zugriffsmodifizierer|Die Zugriffsebene der Depot Form (`public` oder `internal`).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der Quell Code Klasse Attribute hinzuzufügen, die aus dieser Depot Form generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Wenn `True`, werden sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, wird ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die aus der Depot Form (`none`, `abstract` oder `sealed`) generiert wird.|Keiner|
|Basis Depot Form|Die Basisklasse dieser Form.|(keine)|
|-Name|Der Name dieser Form.|Aktueller Name|
|Namespace|Der Namespace, der mit dieser Form verbunden ist.|Aktueller Namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert wird (Fixed, Variable oder None). Wenn ein fester Wert angezeigt wird, wird der Wert der `Fixed Tooltip Text`-Eigenschaft als QuickInfo verwendet. Wenn die Variable ist, wird die QuickInfo in benutzerdefiniertem Code definiert.|Keine|
|Notizen|Informelle Notizen, die dieser Form zugeordnet sind.|\<none>|
|Anfängliche Höhe|Die Anfangshöhe dieser Form in Zoll. Bei Depot Formen ist dies die Höhe des Header Abschnitts und kann nicht geändert werden.|1|
|Anfängliche Breite|Die ursprüngliche Breite dieser Form in Zoll.|1.5|
|Verfügbar gemachte Füllfarbe als Eigenschaft<br /><br /> Offen gelegter Füllverlaufs Modus<br /><br /> Verfügbar gemachte Umriss Farbe als Eigenschaft<br /><br /> Darstellung des Gliederungs Bindestrich Stils als Eigenschaft<br /><br /> Verfügbar gemachte Gliederungs Stärke als Eigenschaft<br /><br /> Macht Textfarbe verfügbar.|Wenn `True`, kann der Benutzer die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Definition, und **Klicken Sie auf**verfügbar machen|False|
|Beschreibung|Wird verwendet, um den generierten Designer zu dokumentieren.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diese Form angezeigt wird.|\<none>|
|Fester QuickInfo-Text|Der Text, der für eine fixierte QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Form verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)