---
title: Eigenschaften von Bildformen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7e492996a194c6602af3ec412b86f7477ef233e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928710"
---
# <a name="properties-of-image-shapes"></a>Eigenschaften von Bildformen
Sie können die Bildformen verwenden, um anzugeben, wie die Domänenklassen in einen generierten Designer angezeigt werden. Definieren Sie eine Bild-Form durch Festlegen der `Image` Eigenschaft der Klasse in einer vordefinierten Image-Datei. Die folgenden Formate werden unterstützt:

- GIF

- JPG

- .JPEG

- .bmp

- WMF

- .EMF

- .png

  Standardmäßig befinden sich Designer Ressourcendateien, wie Bilddateien, in der **Ressourcen**Ordner in der **Dsl** Projekt.

  Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

  Bildformen haben Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Füllfarbe|Die Füllfarbe dieser Form.|Weiß|
|Der Farbverlaufmodus|Die füllverlaufsmodus dieser Form.|Horizontal|
|Verfügt über Standard-Verbindungspunkte|Wenn `True`, verwendet die Form oben, unten, links und rechten Verbindungspunkte im generierten Designer.|False|
|Konturfarbe|Die Konturfarbe dieser Form.|Schwarz|
|Konturstrichstil|Der konturstrichstil dieser Form (einfarbig, Bindestrich, Punkt, DashDot, Strich oder Benutzerdefiniert).|Basis|
|Umrissstärke|Die konturlinienstärke dieser Form.|0.03125|
|Textfarbe|Die Farbe, die für Text-Decorators verwendet wird, die mit dieser Form verknüpft sind.|Schwarz|
|Zugriffsmodifizierer|Der Zugriffsmodifizierer des der Geometrie-Form (öffentlich oder intern).|Public|
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die von dieser Form generiert wird.|\<Keine >|
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse in der Code ein, das mit dem Bild-Form generiert (`none`, `abstract` oder `sealed`).|Keine|
|Basisbildform|Die Basisklasse dieser Form.|(keine)|
|name|Der Name dieser Form.|Aktuelle name|
|Namespace|Der Namespace, der diese Form zugeordnet ist.|Aktuellen namespace|
|QuickInfo-Typ|Der Ort, in dem die QuickInfo definiert ist (fest, Variable oder keine). Wenn fest, klicken Sie dann den Wert des der `Fixed Tooltip Text` Eigenschaft wird als QuickInfo verwendet, wenn die Variable, klicken Sie dann die QuickInfo wird im benutzerdefinierten Code definiert.|Keine|
|Hinweise|Informelle Hinweise, die mit dieser Form verknüpft sind.|\<Keine >|
|Die ursprüngliche Höhe|Die ursprüngliche Höhe dieser Form in Zoll.|1|
|Die ursprüngliche Breite|Die ursprüngliche Breite dieser Form in Zoll.|1.5|
|Als Eigenschaft verfügbar gemachte Füllfarbe<br /><br /> Verfügbar gemachte Füllverlaufsmodus<br /><br /> Konturfarbe als Eigenschaft verfügbar gemacht.<br /><br /> Konturstrichstil als Eigenschaft verfügbar gemacht.<br /><br /> Umrissstärke als Eigenschaft verfügbar<br /><br /> Stellt Text Color|Wenn `True`, der Benutzer kann die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, mit der rechten Maustaste in der Definition der Form, und klicken Sie auf **verfügbare hinzufügen**.|False|
|Beschreibung|Dokumentieren des generierten Designers verwendet.|\<Keine >|
|Anzeigename|Der Name, der im generierten Designer für diese Form angezeigt werden soll.|\<Keine >|
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<Keine >|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Element verwendet wird.|\<Keine >|
|Bild|Der Pfad zur Bilddatei, die für diese Form verwendet wird.|\<Keine >|

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)