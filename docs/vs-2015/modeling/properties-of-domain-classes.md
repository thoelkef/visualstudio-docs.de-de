---
title: Eigenschaften von Domänenklassen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3d5ea3d5cad378a476c9080cd56143b1600b7b4d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513392"
---
# <a name="properties-of-domain-classes"></a>Eigenschaften von Domänenklassen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Eigenschaften von Domänenklassen](https://docs.microsoft.com/visualstudio/modeling/properties-of-domain-classes).  
  
Domänenklassen werden die Eigenschaften in der folgenden Tabelle sind. Weitere Informationen zu den Domänenklassen, finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Zugriffsmodifizierer|Die Zugriffsebene der Domänenklasse (`public` oder `internal`).|`public`|  
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die von dieser Domänenklasse generiert wird.|\<Keine >|  
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse für Code, der von der Domänenklasse generiert wird (`none`, `abstract` oder `sealed`).|`none`|  
|Basisklasse|Wenn diese Domänenklasse abgeleitet ist, den Namen der Basisklasse.|\<Keine >|  
|name|Der Name dieser Domänenklasse.|Aktuelle name|  
|Namespace|Der Namespace dieser Domänenklasse.|Aktuellen namespace|  
|Hinweise|Informelle Hinweise, die mit dieser Domäne verknüpft sind.|\<Keine >|  
|Beschreibung|Die Beschreibung, die zum Dokumentieren der Benutzeroberflächenautomatisierungs des generierten Designers verwendet wird.|\<Keine >|  
|Anzeigename|Der Name, der im generierten Designer für diese Domänenklasse angezeigt wird.|\<Keine >|  
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für diese Domänenklasse verwendet wird.|\<Keine >|  
  
## <a name="see-also"></a>Siehe auch  
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



