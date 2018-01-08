---
title: "Eigenschaften von Domänenklassen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e38000dea9c20f8458fd0f899d43ea8f7c9eb7db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="properties-of-domain-classes"></a>Eigenschaften von Domänenklassen
Domänenklassen haben die Eigenschaften in der folgenden Tabelle. Informationen zu Domänenklassen finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Zugriffsmodifizierer|Die Zugriffsebene der Domänenklasse (`public` oder `internal`).|`public`|  
|Benutzerdefinierte Attribute|Verwendet, um den Code Quellklasse Attribute hinzuzufügen, die von dieser Domänenklasse generiert wird.|\<keine >|  
|Doppelter generiert abgeleitet|Wenn `True`, eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung außer Kraft) generiert werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Verfügt über benutzerdefinierte-Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt werden. Weitere Informationen finden Sie unter [überschreiben und erweitern die generierte Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Inheritance Modifier|Beschreibt die Art der Vererbung von der Quellklasse für Code, der von der Domänenklasse generiert wird (`none`, `abstract` oder `sealed`).|`none`|  
|Basisklasse|Wenn diese Domänenklasse abgeleitet ist, den Namen der Basisklasse.|\<keine >|  
|name|Der Name dieser Domäne-Klasse.|Aktuelle name|  
|Namespace|Der Namespace dieser Domäne-Klasse.|Aktuellen namespace|  
|Hinweise|Informelle Hinweise, die mit dieser Domänenklasse verknüpft sind.|\<keine >|  
|Beschreibung|Die Beschreibung, die verwendet wird, um die Benutzeroberfläche des Designers generierten zu dokumentieren.|\<keine >|  
|Anzeigename|Der Name, der in der generierten Designer für diese Domänenklasse angezeigt wird.|\<keine >|  
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das verwendet wird, um die index-F1-Hilfe für diese Domänenklasse.|\<keine >|  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)