---
title: Eigenschaften von Depot Formen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords: Domain-Specific Language, compartment shape
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 007e1a6468429212ba7d1833157a4c9a2e771652
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-compartment-shapes"></a>Eigenschaften von Depotformen
Depot-Formen sind eine Form, die Sie verwenden können, um eine Domänenklasse in einer domänenspezifischen Sprache anzuzeigen. Sie erweitert und reduziert die Depots.  
  
 Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Depot-Formen besitzen Eigenschaften, die in der folgenden Tabelle aufgeführt sind.  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Standardmäßig erweitern reduzierten Zustand|Wenn `Expanded`, bei der Erstellung der Depots angezeigt. Wenn `Collapsed`, sind Sie nicht.|Erweitert|  
|Füllfarbe|Die Füllfarbe dieser Form.|Weiß|  
|Farbverlauf Füllmodus|Der Farbverlauf Füllmodus dieser Form.|Horizontal|  
|Geometrie|Die Geometrie dieser Form (Rechteck oder abgerundetes Rechteck).|Rechteck|  
|Hat die Standard-Verbindungspunkte|Wenn `True`verwenden der Form "oben, unten, links und rechts Verbindungspunkte im generierten-Designer.|False|  
|Einzelne Depot-Header ist sichtbar|Wenn `False`, und die Form hat einen einzigen Depot, Depot-Header ist nicht sichtbar.|True|  
|Umrissfarbe|Die Konturfarbe dieser Form.|Schwarz|  
|Dash Umrissstil|Das Gliederung Strichformat dieser Form (durchgezogen, Bindestrich, Punkt, DashDot, Strich, benutzerdefinierte).|Basis|  
|Umrissstärke|Die Stärke der Kontur dieser Form.|0.03125|  
|Textfarbe|Die Farbe für Text Decorator-Elementen, die mit dieser Form verknüpft sind.|Schwarz|  
|Zugriffsmodifizierer|Die Zugriffsebene der Depot-Form (`public` oder `internal`).|Public|  
|Benutzerdefinierte Attribute|Verwendet, um den Code Quellklasse Attribute hinzuzufügen, die von dieser Depot-Form generiert wird|\<keine >|  
|Doppelter generiert abgeleitet|Wenn `True`, eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung außer Kraft) generiert werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Verfügt über benutzerdefinierte-Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Inheritance Modifier|Beschreibt die Art der Vererbung von der Quellklasse für Code, der von der Form "Depot" generiert wird (`none`, `abstract` oder `sealed`).|Keine|  
|Basis Depot-Form|Die Basisklasse dieser Form.|(keine)|  
|Name|Der Name dieser Form.|Aktuelle name|  
|Namespace|Der Namespace, der diese Form zugeordnet ist.|Aktuellen namespace|  
|QuickInfo-Typ|Wie die QuickInfo definiert ist (fest, Variable oder keine). Wenn behoben, den Wert der `Fixed Tooltip Text` Eigenschaft wird als QuickInfo verwendet wird und wenn die Variable ist, klicken Sie dann die QuickInfo definiert ist in benutzerdefiniertem Code.|Keine|  
|Hinweise|Informelle Hinweise, die mit dieser Form verknüpft sind.|\<keine >|  
|Anfängliche Höhe|Die anfängliche Höhe dieser Form, in Zoll. Dies ist die Höhe des Headerabschnitts nur Depot-Formen und kann nicht geändert werden.|1|  
|Anfängliche Breite|Die anfängliche Breite dieser Form, in Zoll.|1.5|  
|Als Eigenschaft verfügbar gemachte Füllfarbe<br /><br /> Verfügbar gemachten Füllmodus Farbverlauf<br /><br /> Konturfarbe als Eigenschaft verfügbar gemacht.<br /><br /> Gliederung Strichformat als Eigenschaft verfügbar gemacht.<br /><br /> Umrissstärke als Eigenschaft bereitgestellt<br /><br /> Macht die Textfarbe|Wenn `True`, der Benutzer kann die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, mit der rechten Maustaste der Form "Definition, und klicken Sie auf **hinzufügen verfügbar gemachten**.|False|  
|Beschreibung|So dokumentieren Sie den generierten-Designer verwendet.|\<keine >|  
|Anzeigename|Der Name, der in der generierten Designer für diese Form angezeigt wird.|\<keine >|  
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<keine >|  
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Form verwendet wird.|\<keine >|  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)