---
title: Eigenschaften von Diagrammen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7d669d01339b92c64cfe03ccb3ae897a1816aeac
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701762"
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
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der generierten Codeklasse hinzuzufügen.|\<none>|  
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse für Code, der aus dem Diagramm generiert wird (`none`, `abstract` oder `sealed`).|Keiner|  
|Basisdiagramm|Die Basisklasse des Diagramms.|(keine)|  
|Name|Der Name des Diagramms.|Aktuelle name|  
|Namespace|Der Namespace, der in diesem Diagramm zugeordnet ist.|Aktuellen namespace|  
|Dargestellte Klasse|Die Stamm-Domänenklasse, die in diesem Diagramm darstellt.|Aktuelle Stammklasse ggf.|  
|Hinweise|Informelle Hinweise, die mit diesem Element verknüpft sind.|\<none>|  
|Macht die Füllfarbe als Eigenschaft|Wenn `True`, der Benutzer kann die Füllfarbe des Diagramms des generierten Designers festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Diagrammform, und klicken Sie auf **hinzufügen Explosed**.|False|  
|Textfarbe als Eigenschaft zur Verfügung gestellt|Wenn `True`, der Benutzer kann die Textfarbe des Diagramms im generierten Designer festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Diagrammform, und klicken Sie auf **hinzufügen Explosed**.|False|  
|Beschreibung|Die Beschreibung, die zum Dokumentieren des generierten Designers verwendet wird.|\<none>|  
|Anzeigename|Der Name, der im generierten Designer für dieses Diagramm angezeigt werden soll.|\<none>|  
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Diagramm verwendet wird.|\<none>|  
  
## <a name="see-also"></a>Siehe auch  
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
