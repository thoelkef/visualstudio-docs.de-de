---
title: Eigenschaften des Domänenbeziehungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 48af74aa470f195c1cfbd49ffbabb37e2461251d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263730"
---
# <a name="properties-of-domain-relationships"></a>Eigenschaften von Domänenbeziehungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Eigenschaften in der folgenden Tabelle sind mit einer domänenbeziehung verknüpft. Informationen des domänenbeziehungen finden Sie unter [Grundlegendes zu Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Zugriffsmodifizierer|Die Zugriffsebene der domänenbeziehung (`public` oder `internal`).|`public`|  
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die aus der domänenbeziehung generiert wird.|\<Keine >|  
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) wird generiert. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, gibt an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse für Code, der aus die domänenbeziehung generiert wird (`none`, `abstract` oder `sealed`).|\<Keine >|  
|Duplikate zulässt|Wenn `True`, doppelte Links die domänenbeziehung zwischen den gleichen zwei Elementen erstellt werden kann.|`False`|  
|Basisbeziehungen|Wenn die domänenbeziehung abgeleitet ist, die basisbeziehung die domänenbeziehung.|\<Keine >|  
|Einbetten von ist|Wenn `True`, die domänenbeziehung gibt eine einbettende Beziehung. Wenn `False`, die Beziehung ist eine verweisbeziehung.|\<Beide >|  
|name|Der Name der domänenbeziehung.|Aktuelle name|  
|Namespace|Der Namespace, der die domänenbeziehung zugeordnet ist.|Aktuellen namespace|  
|Hinweise|Informelle Hinweise, die die domänenbeziehung zugeordnet sind.|\<Keine >|  
|Beschreibung|Die Beschreibung, die wird verwendet, um Code zu dokumentieren, die in der Benutzeroberfläche des generierten Designers verwendet wird.|\<Keine >|  
|Anzeigename|Der Name, der im generierten Designer für die domänenbeziehung angezeigt wird.|\<Keine >|  
|Hilfsschlüsselwort|Das optionale Schlüsselwort, das zum Indizieren der F1-Hilfe für die domänenbeziehung verwendet wird.|\<Keine >|  
  
## <a name="see-also"></a>Siehe auch  
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



