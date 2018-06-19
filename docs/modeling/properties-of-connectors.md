---
title: Eigenschaften von Konnektoren
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: e8954727d7ee38b81ba5993b41e300ef1c6d66fc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31952730"
---
# <a name="properties-of-connectors"></a>Eigenschaften von Konnektoren
Verbinder repräsentieren domänenbeziehungen in einem generierten Designer.

 Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Connectors wurden die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|Beschreibung|Standard|
|--------------|-----------------|-------------|
|Farbe|Die Farbe der diesen Connector.|Schwarz|
|Strichformat|Das Strichformat für die Zeile für diesen Connector (durchgezogen, Bindestrich, Punkt, DashDot, Strich oder Benutzerdefiniert).|Basis|
|Source-End-Stil|Die Quelle End Formatvorlage für diesen Connector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond oder keine).|Keiner|
|Ziel-End-Stil|Der Ziel-End-Stil für diesen Connector (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond oder keine).|Keiner|
|Textfarbe|Die Farbe, die für Text Decorator-Elementen verwendet wird, die mit diesem Connector verknüpft sind.|Schwarz|
|Stärke|Die Stärke der Linie für diesen Connector, gemessen in Zoll.|0.03125|
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse (`public` oder `internal`).|Public|
|Benutzerdefinierte Attribute|Verwendet, um den Code Quellklasse Attribute hinzuzufügen, die von diesem Connector generiert wird.|\<keine >|
|Doppelter generiert abgeleitet|Wenn `True`, eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung außer Kraft) generiert werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Verfügt über benutzerdefinierte-Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Inheritance Modifier|Beschreibt die Art der Vererbung von der Quellklasse für Code, der vom Connector generiert wird (`none`, `abstract` oder `sealed`).|Keine|
|Basis-Connector|Die Basisklasse dieses Connectors.|(keine)|
|name|Der Name dieses Connectors.|Aktuelle name|
|Namespace|Der Namespace, der dieser Verbindung zugeordnet ist.|Aktuellen namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert ist (fest, Variable oder keine). Wenn behoben, den Wert der `Fixed Tooltip Text` Eigenschaft wird als QuickInfo verwendet wird und wenn die Variable ist, klicken Sie dann die QuickInfo definiert ist in benutzerdefiniertem Code.|\<keine >|
|Hinweise|Informelle Hinweise, die mit diesem Connector verknüpft sind.|\<keine >|
|Routing-Stil|Das Format, das für das routing des Connectors verwendet wird. Ein `Rectilinear` Connector macht Rechtwinklige schaltet nach Bedarf; eine `Straight` Connector nicht.|Achtzackiger geradliniger|
|Als Eigenschaft verfügbar gemachte Farbe<br /><br /> Als Eigenschaft verfügbar gemachte Strichformat<br /><br /> Als Eigenschaft verfügbar gemachte Stärke<br /><br /> Macht die Textfarbe|Wenn `True`, der Benutzer kann die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, mit der rechten Maustaste der Form "Definition, und klicken Sie auf **hinzufügen verfügbar gemachten**.|False|
|Beschreibung|So dokumentieren Sie den generierten-Designer verwendet.|\<keine >|
|Anzeigename|Der Name, der in der generierten Designer für diesen Connector angezeigt wird.|\<keine >|
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<keine >|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Element verwendet wird.|\<keine >|

## <a name="see-also"></a>Siehe auch

- [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)