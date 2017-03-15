---
title: "Eigenschaften von Anschlussformen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.port"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Anschluss-Form"
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Eigenschaften von Anschlussformen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können mithilfe von Port im generierten Klassen Domänen Designers darzustellen.  
  
 Weitere Informationen finden Sie unter [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)verwendet.  
  
 Port Formen verfügen über Eigenschaften, die in der folgenden Tabelle aufgelistet sind.  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|Füllfarbe|Die Füllfarbe dieser Form.|Weiß|  
|Füllbereichs\-Farbverlaufs\-Modus|Der Modus Farbverlauf Füllen dieser Form.|Horizontal|  
|Geometry|Die Geometrie dieser Form \(Rechteck, abgerundetes Rechteck oder Kreis, Ellipse\).|Rechteck|  
|Hat Standardwert von Verbindungspunkten|Wenn `True`, die im oberen, unteren, linken und rechten Verbindungspunkte im generierten Designer verwenden.|False|  
|Umrissfarbe|Die Umrissfarbe dieser Form.|Black|  
|Konturen\-Bindestrich\-Format|Das Format dieser Form \(bindestrich Kontur Durchgezogen, Bindestriche, zeigen, DashDot DashDotDot, oder benutzerdefiniert\).|Durchgezogen|  
|Konturen\-Stärke|Die Kontur stärke dieser Form.|0.03125|  
|Textfarbe|Die Farbe, die für Text decorator\-elemente verwendet wird, die mit diesem Formular verknüpft sind.|Black|  
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse \(`public` oder `internal`\).|Public|  
|Benutzerdefinierte Attribute|Wird verwendet, um Attribute der Quellcode Klasse hinzufügen, die von diesem Formular generiert wird.|\<Keine\>|  
|Generiert doppeltes abgeleitetes|Wenn `True`, eine Basisklasse und eine partielle Klasse \(Anpassung von Überschreibungen unterstützen\) generiert wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md)|False|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung der Quellcode \- Klasse, die aus dem Port generiert wird \(`none`, `abstract` oder `sealed`\).|Keine|  
|Niedriger Anschluss|Die Basisklasse dieser Form.|\(kein\)|  
|Name|Der Name dieser Form.|Aktueller Name|  
|Namespace|Der Namespace, der mit diesem Formular verbunden ist.|Aktueller Namespace|  
|QuickInfo\-Typ|Wie die QuickInfo definiert ist \(korrigiert, Variablen oder keine\).  Wenn er korrigiert, und anschließend wird, wird der Wert der `Fixed Tooltip Text`\-Eigenschaft als QuickInfo verwendet. Variablen\-, wenn die QuickInfo dann im benutzerdefinierten Code definiert ist.|Keine|  
|Hinweise|Informelle Hinweise, die dieser Form zugeordnet sind.|\<Keine\>|  
|Der anfängliche Höhe|Die Ausgangshöhe dieser Form, in Zoll.|1|  
|Der anfängliche Breite|Die Ausgangsbreite dieser Form, in Zoll.|1.5|  
|Füllfarbe als Eigenschaft verfügbar gemachte<br /><br /> Füllbereichs\-Farbverlaufs\-Modus verfügbar gemachte<br /><br /> Umrissfarbe als Eigenschaft verfügbar gemachte<br /><br /> Konturen\-Bindestrich\-Format als Eigenschaft verfügbar gemachte<br /><br /> Konturen\-Stärke als Eigenschaft verfügbar gemachte<br /><br /> Exposee\-Textfarbe|Wenn `True`, der Benutzer die angegebene Eigenschaft ein Formular festlegen kann.  Wenn Sie dies mit der rechten Maustaste auf die Form, und klicken Sie auf Definition **Verfügbar gemacht hinzufügen**festlegen.|False|  
|Beschreibung|Ein Dokument den generierten Designer verwenden.|\<Keine\>|  
|Angezeigter Name|Der Name, der im generierten Designer für diese Form angezeigt wird.|\<Keine\>|  
|Fester QuickInfo\-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<Keine\>|  
|Hilfeschlüsselwort|Das Schlüsselwort, das dem Index F1\-Hilfe für diese Form verwendet wird.|\<Keine\>|  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)