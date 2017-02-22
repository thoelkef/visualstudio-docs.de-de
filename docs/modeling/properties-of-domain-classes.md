---
title: "Eigenschaften von Dom&#228;nenklassen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Domänenklasse"
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Eigenschaften von Dom&#228;nenklassen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Domänen Klassen verfügen die Eigenschaften in der folgenden Tabelle.  Weitere Informationen über Domänen Klassen finden Sie unter [Grundlagen von Modellen, Klassen und Beziehungen](../modeling/understanding-models-classes-and-relationships.md).  Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)verwendet.  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|Zugriffsmodifizierer|Die Zugriffsebene der Domänenklasse \(`public` oder `internal`\).|`public`|  
|Benutzerdefinierte Attribute|Wird verwendet, um Attribute der Quellcode Klasse hinzufügen, die von dieser Domänenklasse generiert wird.|\<Keine\>|  
|Generiert doppeltes abgeleitetes|Wenn `True`, eine Basisklasse und eine partielle Klasse \(Anpassung von Überschreibungen unterstützen\) generiert wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung der Quellcode Klasse, die von der Domänenklasse generiert wird \(`none`, `abstract` oder `sealed`\).|`none`|  
|Basisklasse|Wenn diese Domänenklasse abgeleitet ist, der Name der Basisklasse.|\<Keine\>|  
|Name|Der Name dieser Domänenklasse.|Aktueller Name|  
|Namespace|Der Namespace dieser Domänenklasse.|Aktueller Namespace|  
|Hinweise|Informelle Hinweise, die dieser Domänenklasse zugeordnet sind.|\<Keine\>|  
|Beschreibung|Die Beschreibung, die dem Dokument generierten die Benutzeroberfläche des Designers verwendet wird.|\<Keine\>|  
|Angezeigter Name|Der Name, der im generierten Designer für diese Domänenklasse angezeigt wird.|\<Keine\>|  
|Hilfeschlüsselwort|Das optionale Schlüsselwort, das in Index F1\-Hilfe für diese Domänenklasse verwendet wird.|\<Keine\>|  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)