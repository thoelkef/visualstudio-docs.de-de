---
title: "Eigenschaften von Diagrammen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Diagramm"
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# Eigenschaften von Diagrammen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Eigenschaften festlegen, die angeben, wie die Diagramme im generierten Designer angezeigt werden.  Beispielsweise können Sie eine Standardfarbe für Text im Diagramm angeben.  
  
 Weitere Informationen finden Sie unter [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)verwendet.  
  
 In der folgenden Tabelle werden die Eigenschaften von Diagrammen auf.  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|Füllfarbe|Die Füllfarbe für das Diagramm.|Weiß|  
|Textfarbe|Die Farbe des Texts im Diagramm angezeigt wird.|Black|  
|Zugriffsmodifizierer|Der Zugriffsmodifizierer öffentlich oder der Klasse \(internal\).|Public|  
|Benutzerdefinierte Attribute|Wird verwendet, um Attribute der generierten Codeklasse hinzuzufügen.|\<Keine\>|  
|Generiert doppeltes abgeleitetes|Wenn `True`, eine Basisklasse und eine partielle Klasse \(Anpassung von Überschreibungen unterstützen\) generiert wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung der Quellcode Klasse, die aus dem Diagramm generiert wird \(`none`, `abstract` oder `sealed`\).|None|  
|Niedriges Diagramm|Die Basisklasse des Diagramms.|\(kein\)|  
|Name|Der Name dieses Diagramms.|Aktueller Name|  
|Namespace|Der Namespace, der mit diesem Diagramm verbunden ist.|Aktueller Namespace|  
|Klasse dargestellt.|Die Stammdomänen Klasse, die dieses Diagramm darstellt.|Aktuelle Stammklasse falls zutreffend|  
|Hinweise|Informelle Hinweise, die diesem Element zugeordnet sind.|\<Keine\>|  
|Exposee\-Füllfarbe als Eigenschaft|Wenn `True`, der Benutzer die Füllfarbe des Diagramms des generierten Designers festlegen kann.  Um dieses Diagramm mit der rechten Maustaste auf die Form, und klicken Sie auf **Verfügbar gemacht hinzufügen**festlegen.|False|  
|Exposee\-Textfarbe als Eigenschaft|Wenn `True`, der Benutzer die Textfarbe des Diagramms im generierten Designer festlegen können.  Um dieses Diagramm mit der rechten Maustaste auf die Form, und klicken Sie auf **Verfügbar gemacht hinzufügen**festlegen.|False|  
|Beschreibung|Die Beschreibung, die an das Dokument der generierte Designer verwendet wird.|\<Keine\>|  
|Angezeigter Name|Der Name, der im generierten Designer für dieses Diagramm angezeigt wird.|\<Keine\>|  
|Hilfeschlüsselwort|Das Schlüsselwort, das dem Index F1\-Hilfe für das Diagramm verwendet wird.|\<Keine\>|  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)