---
title: Eigenschaften von Konnektoren
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9ae6a15f554b9eba3a6a9144efbb4dffa8e8ae89
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942228"
---
# <a name="properties-of-connectors"></a>Eigenschaften von Konnektoren
Verbinder repräsentieren domänenbeziehungen in einen generierten Designer.

 Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Connectors verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|Farbe|Die Farbe dieses Verbinders.|Schwarz|
|Dash-Format|Der Strichstil für die Zeile für diesen Connector (einfarbig, Bindestrich, Punkt, DashDot, Strich oder Benutzerdefiniert).|Basis|
|Quellendlinienstärke|Die quellendlinienstärke für diesen Connector (HollowArrow EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond oder keine).|Keine|
|Zielendlinienart|Die zielendlinienart für diesen Connector (HollowArrow EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond oder keine).|Keine|
|Textfarbe|Die Farbe, die für Text-Decorators verwendet wird, die mit diesem Connector verknüpft sind.|Schwarz|
|Stärke|Die Stärke der Linie für dieses Verbinders, gemessen in Zoll.|0.03125|
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse (`public` oder `internal`).|Public|
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die von diesem Connector generiert wird.|\<none>|
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse in der Code ein, die vom Connector generiert wird (`none`, `abstract` oder `sealed`).|none|
|Basisverbinder|Die Basisklasse dieses Verbinders.|(keine)|
|name|Der Name dieses Verbinders.|Aktuelle name|
|Namespace|Der Namespace, der diesen Connector zugeordnet ist.|Aktuellen namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert ist (fest, Variable oder keine). Wenn fest, klicken Sie dann den Wert des der `Fixed Tooltip Text` Eigenschaft wird als QuickInfo verwendet, wenn die Variable, klicken Sie dann die QuickInfo wird im benutzerdefinierten Code definiert.|\<none>|
|Hinweise|Informelle Hinweise, die mit diesem Connector verknüpft sind.|\<none>|
|Routingstil|Der Stil, der für das routing des Connectors verwendet wird. Ein `Rectilinear` Connector stellt Rechtwinklige Durchgängen erforderlich; eine `Straight` Verbinder nicht.|Pfeilspitzentypen zur Verfügung stehen|
|Verfügbar gemachte Farbe als Eigenschaft<br /><br /> Als Eigenschaft verfügbar gemachte Strichstil<br /><br /> Die Stärke als Eigenschaft verfügbar gemacht<br /><br /> Stellt Text Color|Wenn `True`, der Benutzer kann die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, mit der rechten Maustaste in der Definition der Form, und klicken Sie auf **verfügbare hinzufügen**.|False|
|Beschreibung|Dokumentieren des generierten Designers verwendet.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diesen Connector angezeigt wird.|\<none>|
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Element verwendet wird.|\<none>|

## <a name="see-also"></a>Siehe auch

- [DSL-Tools – Glossar](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)