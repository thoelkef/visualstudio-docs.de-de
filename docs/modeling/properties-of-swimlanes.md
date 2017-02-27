---
title: "Eigenschaften von Verantwortlichkeitsbereichen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.swimlane"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Verantwortlichkeitsbereich"
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Eigenschaften von Verantwortlichkeitsbereichen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Verantwortlichkeitsbereiche einem Diagramm hinzufügen.  Swimlanes\-Verteilung ein Diagramm in die horizontale oder vertikale Bereiche.  Sie können innerhalb der Verantwortlichkeitsbereiche Formen angezeigt werden, andere definieren.  Weitere Informationen finden Sie unter [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)verwendet.  
  
 Swimlanes verfügen über Eigenschaften, die in der folgenden Tabelle aufgelistet sind.  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|Text\-Füllfarbe|Die Füllfarbe für den Text des swimlane.|Weiß|  
|Header\-Füllfarbe|Die Füllfarbe für den Header des swimlane.|Dunkelgrau|  
|Trennzeichen\-Farbe|Die Farbe der Trennlinie.|Hellgrau|  
|Trennlinien\-Format|Das Format der Trennlinie \(`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`oder `Custom`\).|`Dash`|  
|Trennzeichen\-Stärke|Die Stärke der Trennlinie in Zoll.|0.03125|  
|Textfarbe|Die Farbe, die für Text decorator\-elemente verwendet wird, die mit diesem swimlane zugeordnet sind.|Black|  
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse \(`public` oder `internal`\).|Public|  
|Benutzerdefinierte Attribute|Wird verwendet, um Attribute der Codeklasse hinzugefügt werden soll, die von diesem swimlane generiert wird.|\<Keine\>|  
|Generiert doppeltes abgeleitetes|Wenn `True`, eine Basisklasse und eine partielle Klasse \(Anpassung von Überschreibungen unterstützen\) generiert wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung der Quellcode Klasse, die vom swimlane generiert wird \(`none`, `abstract` oder `sealed`\).|Keine|  
|Niedriges Swimlane|Die Basisklasse dieser swimlane.|\(kein\)|  
|Name|Der Name dieses swimlane.|Aktueller Name|  
|Namespace|Der Namespace, der diesem swimlane verbunden ist.|Aktueller Namespace|  
|QuickInfo\-Typ|Wie die QuickInfo definiert ist \(`fixed`, `variable`oder `none`\).  Wenn `fixed`, wird der Wert der `Fixed Tooltip Text`\-Eigenschaft verwendet wird. `variable`, wenn die QuickInfo dann im benutzerdefinierten Code definiert ist.|\<Keine\>|  
|Hinweise|Informelle Anmerkungen, die diesem swimlane zugeordnet sind.|\<Keine\>|  
|Ausrichtung|Horizontal oder vertikale Ausrichtung.|Vertikal|  
|Der anfängliche Höhe|Die Ausgangshöhe des swimlane, in Zoll.  Anwendbar nur den horizontalen Verantwortlichkeitsbereiche.|0|  
|Der anfängliche Breite|Die ursprüngliche Breite dieses swimlane, in Zoll.  Anwendbar auf den vertikalen Verantwortlichkeitsbereiche.|0|  
|Exposee\-Textfarbe|Wenn `True`, der Benutzer die Farbe eines swimlane im generierten Designer festlegen können.  Wenn Sie dies mit der rechten Maustaste auf die swimlane Form, und klicken Sie auf **Verfügbar gemacht hinzufügen**festlegen.|False|  
|Beschreibung|Ein Dokument den generierten Designer verwenden.|\<Keine\>|  
|Angezeigter Name|Der Name, der im generierten Designer angezeigt wird, um diese swimlane Klasse zuzugreifen.|\<Keine\>|  
|Fester QuickInfo\-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<Keine\>|  
|Hilfeschlüsselwort|Das Schlüsselwort, das dem Index F1\-Hilfe für dieses swimlane verwendet wird.|\<Keine\>|  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)