---
title: Eigenschaften von Diagrammen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: bd02bd7f91d80392553d4c9f5e7ff10ab71b1abe
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-diagrams"></a>Eigenschaften von Diagrammen
Sie können Eigenschaften festlegen, die angeben, wie Diagramme in der generierten-Designer angezeigt werden. Sie können z. B. eine Standardfarbe für Text in das Diagramm angeben.

 Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Die folgende Tabelle enthält die Eigenschaften der Diagramme.

|Eigenschaft|Beschreibung|Standard|
|--------------|-----------------|-------------|
|Füllfarbe|Die Füllfarbe für das Diagramm.|Weiß|
|Textfarbe|Die Farbe des Texts, der im Diagramm angezeigt wird.|Schwarz|
|Zugriffsmodifizierer|Der Zugriffsmodifizierer der Klasse ("public" oder "internal").|Öffentlich|
|Benutzerdefinierte Attribute|Verwendet den generierten Codeklasse Attribute hinzu.|\<keine >|
|Doppelter generiert abgeleitet|Wenn `True`, eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung außer Kraft) generiert werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Verfügt über benutzerdefinierte-Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md)...|False|
|Inheritance Modifier|Beschreibt die Art der Vererbung von der Quellklasse für Code, der aus dem Diagramm generiert wird (`none`, `abstract` oder `sealed`).|Keine|
|Basis-Diagramm|Die Basisklasse von diesem Diagramm.|(keine)|
|Name|Der Name des in diesem Diagramm.|Aktuelle name|
|Namespace|Der Namespace, der in diesem Diagramm zugeordnet ist.|Aktuellen namespace|
|Klasse dargestellt wird|Der Stamm-Domäne-Klasse, die in diesem Diagramm darstellt.|Aktuelle Stammklasse ggf.|
|Notizen|Informelle Hinweise, die mit diesem Element zugeordnet sind.|\<keine >|
|Macht die Füllfarbe als Eigenschaft|Wenn `True`, der Benutzer kann die Füllfarbe des Diagramms generierten-Designer festlegen. Um dies festzulegen, klicken Sie mit der mit der rechten Maustaste auf die Form "Diagramm", und klicken Sie auf **hinzufügen Explosed**.|False|
|Textfarbe als Eigenschaft verfügbar gemacht.|Wenn `True`, der Benutzer kann die Textfarbe des Diagramms im generierten-Designer festlegen. Um dies festzulegen, klicken Sie mit der mit der rechten Maustaste auf die Form "Diagramm", und klicken Sie auf **hinzufügen Explosed**.|False|
|Beschreibung|Die Beschreibung, die verwendet wird, um den generierten-Designer zu dokumentieren.|\<keine >|
|Anzeigename|Der Name, der in der generierten Designer für dieses Diagramm angezeigt wird.|\<keine >|
|Hilfsschlüsselwort|Das Schlüsselwort, das verwendet wird, um die F1-Hilfe für das Diagramm zu indizieren.|\<keine >|

## <a name="see-also"></a>Siehe auch

- [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)