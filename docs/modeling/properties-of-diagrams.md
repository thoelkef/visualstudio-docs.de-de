---
title: Eigenschaften von Diagrammen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c00ec651510da84594c370e312112c50bc545606
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="properties-of-diagrams"></a>Eigenschaften von Diagrammen
Sie können Eigenschaften festlegen, die angeben, wie Diagramme in der generierten-Designer angezeigt werden. Sie können z. B. eine Standardfarbe für Text in das Diagramm angeben.  
  
 Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Die folgende Tabelle enthält die Eigenschaften der Diagramme.  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Füllfarbe|Die Füllfarbe für das Diagramm.|Weiß|  
|Textfarbe|Die Farbe des Texts, der im Diagramm angezeigt wird.|Schwarz|  
|Zugriffsmodifizierer|Der Zugriffsmodifizierer der Klasse ("public" oder "internal").|Public|  
|Benutzerdefinierte Attribute|Verwendet den generierten Codeklasse Attribute hinzu.|\<keine >|  
|Doppelter generiert abgeleitet|Wenn `True`, eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung außer Kraft) generiert werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Verfügt über benutzerdefinierte-Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Inheritance Modifier|Beschreibt die Art der Vererbung von der Quellklasse für Code, der aus dem Diagramm generiert wird (`none`, `abstract` oder `sealed`).|Keiner|  
|Basis-Diagramm|Die Basisklasse von diesem Diagramm.|(keine)|  
|name|Der Name des in diesem Diagramm.|Aktuelle name|  
|Namespace|Der Namespace, der in diesem Diagramm zugeordnet ist.|Aktuellen namespace|  
|Klasse dargestellt wird|Der Stamm-Domäne-Klasse, die in diesem Diagramm darstellt.|Aktuelle Stammklasse ggf.|  
|Hinweise|Informelle Hinweise, die mit diesem Element zugeordnet sind.|\<keine >|  
|Macht die Füllfarbe als Eigenschaft|Wenn `True`, der Benutzer kann die Füllfarbe des Diagramms generierten-Designer festlegen. Um dies festzulegen, klicken Sie mit der mit der rechten Maustaste auf die Form "Diagramm", und klicken Sie auf **hinzufügen Explosed**.|False|  
|Textfarbe als Eigenschaft verfügbar gemacht.|Wenn `True`, der Benutzer kann die Textfarbe des Diagramms im generierten-Designer festlegen. Um dies festzulegen, klicken Sie mit der mit der rechten Maustaste auf die Form "Diagramm", und klicken Sie auf **hinzufügen Explosed**.|False|  
|Beschreibung|Die Beschreibung, die verwendet wird, um den generierten-Designer zu dokumentieren.|\<keine >|  
|Anzeigename|Der Name, der in der generierten Designer für dieses Diagramm angezeigt wird.|\<keine >|  
|Hilfsschlüsselwort|Das Schlüsselwort, das verwendet wird, um die F1-Hilfe für das Diagramm zu indizieren.|\<keine >|  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)