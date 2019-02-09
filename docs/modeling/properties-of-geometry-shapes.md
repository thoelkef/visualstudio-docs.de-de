---
title: Eigenschaften geometrischer Formen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b1006fdb766c4c375c93a97f17cccd4e95568677
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937255"
---
# <a name="properties-of-geometry-shapes"></a>Eigenschaften geometrischer Formen
Sie können Geometrie-Formen verwenden, um anzugeben, wie Instanzen von Domänenklassen in einer domänenspezifischen Sprache angezeigt werden. Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Geometrischer Formen haben Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Füllfarbe|Die Füllfarbe dieser Form.|Weiß|
|Der Farbverlaufmodus|Die füllverlaufsmodus dieser Form (Horizontal, vertikal, vorwärts Diagonal, rückwärts Diagonal oder keine).|Horizontal|
|Geometry|Die Geometrie dieser Form (Rechteck, abgerundetes Rechteck, Ellipse oder Kreis).|Rechteck|
|Verfügt über Standard-Verbindungspunkte|Wenn `True`, verwendet die Form oben, unten, links und rechten Verbindungspunkte im generierten Designer.|False|
|Konturfarbe|Die Konturfarbe dieser Form.|Schwarz|
|Konturstrichstil|Der konturstrichstil dieser Form (einfarbig, Bindestrich, Punkt, DashDot, Strich oder Benutzerdefiniert).|Basis|
|Umrissstärke|Die konturlinienstärke dieser Form.|0.03125|
|Textfarbe|Die Farbe, die für Text-Decorators verwendet wird, die mit dieser Form verknüpft sind.|Schwarz|
|Zugriffsmodifizierer|Der Zugriffsmodifizierer der-Klasse (öffentlich oder intern).|Public|
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die für diese Form generiert wird.|\<none>|
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse für Code, der von der Form generiert wird (`none`, `abstract` oder `sealed`).|none|
|Basisgeometrieform|Die Basisklasse dieser Form.|(keine)|
|name|Der Name dieser Form.|Aktuelle name|
|Namespace|Der Namespace, der diese Form zugeordnet ist.|Aktuellen namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert ist (fest, Variable oder keine). Wenn fest, klicken Sie dann den Wert des der `Fixed Tooltip Text` Eigenschaft wird als QuickInfo verwendet, wenn die Variable, klicken Sie dann die QuickInfo wird im benutzerdefinierten Code definiert.|Keine|
|Hinweise|Informelle Hinweise, die mit diesem Element verknüpft sind.|\<none>|
|Die ursprüngliche Höhe|Die ursprüngliche Höhe dieser Form in Zoll.|1|
|Die ursprüngliche Breite|Ursprüngliche Breite dieser Form in Zoll.|1.5|
|Als Eigenschaft verfügbar gemachte Füllfarbe<br /><br /> Verfügbar gemachte Füllverlaufsmodus<br /><br /> Konturfarbe als Eigenschaft verfügbar gemacht.<br /><br /> Konturstrichstil als Eigenschaft verfügbar gemacht.<br /><br /> Umrissstärke als Eigenschaft verfügbar<br /><br /> Stellt Text Color|Wenn `True`, der Benutzer kann die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, mit der rechten Maustaste in der Definition der Form, und klicken Sie auf **verfügbare hinzufügen**.|False|
|Beschreibung|Die Beschreibung, die zum Dokumentieren des generierten Designers verwendet wird.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diese Form angezeigt werden soll.|\<none>|
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Form verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)