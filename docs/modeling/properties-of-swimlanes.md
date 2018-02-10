---
title: Eigenschaften von Verantwortlichkeitsbereichen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 39bb6be4146cf7e9e163b6da5ada6f447a930bc8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-swimlanes"></a>Eigenschaften von Verantwortlichkeitsbereichen
Sie können ein Diagramm Verantwortlichkeitsbereiche hinzufügen. Verantwortlichkeitsbereiche werden ein Diagramm in vertikale oder horizontale Bereiche unterteilt. Sie können andere Formen innerhalb Verantwortlichkeitsbereiche anzuzeigende definieren. Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Verantwortlichkeitsbereiche haben Eigenschaften, die in der folgenden Tabelle aufgeführt sind.  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Füllfarbe Text|Die Füllfarbe für den Hauptteil der Verantwortlichkeitsbereich.|Weiß|  
|Header-Füllfarbe|Die Füllfarbe für den die Verantwortlichkeitsbereich-Header.|DarkGray|  
|Trennzeichenfarbe|Die Farbe der Linie als Trennzeichen.|LightGray|  
|Linienart Trennzeichen|Der Stil der Linie als Trennzeichen (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, oder `Custom`).|`Dash`|  
|Trennzeichen Stärke|Die Stärke der Linie als Trennzeichen in Zoll.|0.03125|  
|Textfarbe|Die Farbe, die für Text Decorator-Elementen verwendet wird, die diese Verantwortlichkeitsbereich zugeordnet sind.|Schwarz|  
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse (`public` oder `internal`).|Public|  
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Klasse Code hinzuzufügen, die von diesem Verantwortlichkeitsbereich generiert wird.|\<keine >|  
|Doppelter generiert abgeleitet|Wenn `True`, eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung außer Kraft) generiert werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Verfügt über benutzerdefinierte-Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Inheritance Modifier|Beschreibt die Art der Vererbung der Source-Code-Klasse, die aus dem Verantwortlichkeitsbereich generiert wird (`none`, `abstract` oder `sealed`).|Keine|  
|Basis Verantwortlichkeitsbereich|Die Basisklasse von diesem Verantwortlichkeitsbereich.|(keine)|  
|name|Der Name der dieser Verantwortlichkeitsbereich.|Aktuelle name|  
|Namespace|Der Namespace, der diese Verantwortlichkeitsbereich zugeordnet ist.|Aktuellen namespace|  
|QuickInfo-Typ|Wie die QuickInfo definiert ist (`fixed`, `variable`, oder `none`). Wenn `fixed`, klicken Sie dann den Wert von der `Fixed Tooltip Text` Eigenschaft verwendet wird, wenn `variable`, und klicken Sie dann die QuickInfo in benutzerdefiniertem Code definiert ist.|\<keine >|  
|Hinweise|Informelle Hinweise, die diese Verantwortlichkeitsbereich zugeordnet sind.|\<keine >|  
|Ausrichtung|Horizontale oder vertikale Ausrichtung.|Vertikal|  
|Anfängliche Höhe|Die anfängliche Höhe dieses Verantwortlichkeitsbereich, in Zoll. Gilt nur für horizontale Verantwortlichkeitsbereiche.|0|  
|Anfängliche Breite|Die anfängliche Breite von diesem Verantwortlichkeitsbereich, in Zoll. Gilt nur für vertikale Verantwortlichkeitsbereiche.|0|  
|Macht die Textfarbe|Wenn `True`, der Benutzer kann die Farbe des ein Verantwortlichkeitsbereich im generierten-Designer festlegen. Um dies festzulegen, mit der rechten Maustaste in der Form "Verantwortlichkeitsbereich", und klicken Sie auf **hinzufügen verfügbar gemachten**.|False|  
|Beschreibung|So dokumentieren Sie den generierten-Designer verwendet.|\<keine >|  
|Anzeigename|Der Name, der in der generierten Designer zum Verweisen auf diese Klasse Verantwortlichkeitsbereich angezeigt wird.|\<keine >|  
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<keine >|  
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Verantwortlichkeitsbereich verwendet wird.|\<keine >|  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)