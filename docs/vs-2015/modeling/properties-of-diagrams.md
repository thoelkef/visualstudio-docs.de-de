---
title: Eigenschaften von Diagrammen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9db932bb5e19cdc10dde3cd8330c4a57208a0c2d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280903"
---
# <a name="properties-of-diagrams"></a>Eigenschaften von Diagrammen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Eigenschaften festlegen, die angeben, wie Diagramme im generierten Designer angezeigt werden. Beispielsweise können Sie eine Standardfarbe für Text in das Diagramm angeben.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Die folgende Tabelle enthält die Eigenschaften von Diagrammen.  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Füllfarbe|Die Füllfarbe für das Diagramm.|Weiß|  
|Textfarbe|Die Farbe des Texts, der im Diagramm angezeigt wird.|Schwarz|  
|Zugriffsmodifizierer|Der Zugriffsmodifizierer der-Klasse (öffentlich oder intern).|Public|  
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der generierten Codeklasse hinzuzufügen.|\<Keine >|  
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse für Code, der aus dem Diagramm generiert wird (`none`, `abstract` oder `sealed`).|Keiner|  
|Basisdiagramm|Die Basisklasse des Diagramms.|(keine)|  
|name|Der Name des Diagramms.|Aktuelle name|  
|Namespace|Der Namespace, der in diesem Diagramm zugeordnet ist.|Aktuellen namespace|  
|Dargestellte Klasse|Die Stamm-Domänenklasse, die in diesem Diagramm darstellt.|Aktuelle Stammklasse ggf.|  
|Hinweise|Informelle Hinweise, die mit diesem Element verknüpft sind.|\<Keine >|  
|Macht die Füllfarbe als Eigenschaft|Wenn `True`, der Benutzer kann die Füllfarbe des Diagramms des generierten Designers festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Diagrammform, und klicken Sie auf **hinzufügen Explosed**.|False|  
|Textfarbe als Eigenschaft zur Verfügung gestellt|Wenn `True`, der Benutzer kann die Textfarbe des Diagramms im generierten Designer festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Diagrammform, und klicken Sie auf **hinzufügen Explosed**.|False|  
|Beschreibung|Die Beschreibung, die zum Dokumentieren des generierten Designers verwendet wird.|\<Keine >|  
|Anzeigename|Der Name, der im generierten Designer für dieses Diagramm angezeigt werden soll.|\<Keine >|  
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Diagramm verwendet wird.|\<Keine >|  
  
## <a name="see-also"></a>Siehe auch  
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



