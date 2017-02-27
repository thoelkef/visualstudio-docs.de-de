---
title: "Eigenschaften von Konnektoren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Verbindungen"
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Eigenschaften von Konnektoren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Domänen\-Verhältnisse stellen Verbindungen in einem generierten Designer dar.  
  
 Weitere Informationen finden Sie unter [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)verwendet.  
  
 Verbindungen verfügen über Eigenschaften, die in der folgenden Tabelle aufgelistet sind.  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|Farbe|Die Farbe des Konnektors.|Black|  
|Bindestrich\-Format|Das Bindestriche Format für die Zeile für den Konnektor \(Durchgezogen, Bindestriche, zeigen, DashDot, DashDotDot oder benutzerdefiniert\).|Durchgezogen|  
|Quell\-Enden\-Format|Das Format für diesen Connector Beenden Sources \(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond FilledDiamond, oder None\).|None|  
|Ziel\-Enden\-Format|Das Ziel beenden HollowArrow Format für den Konnektor \(EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, oder None\).|None|  
|Textfarbe|Die Farbe, die für Text decorator\-elemente verwendet wird, die mit diesem Konnektor zugeordnet sind.|Black|  
|Thickness|Die Stärke der Linie für diesen Connector, gemessen in Zoll.|0.03125|  
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse \(`public` oder `internal`\).|Public|  
|Benutzerdefinierte Attribute|Wird verwendet, um Attribute der Quellcode Klasse hinzufügen, die von diesen Connector generiert wird.|\<Keine\>|  
|Generiert doppeltes abgeleitetes|Wenn `True`, eine Basisklasse und eine partielle Klasse \(Anpassung von Überschreibungen unterstützen\) generiert wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird.  Weitere Informationen finden Sie unter [Überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung der Quellcode Klasse, die vom Konnektor \(`none`generiert wird, oder `abstract``sealed`\).|Keine|  
|Niedriger Konnektor|Die Basisklasse des Konnektors.|\(kein\)|  
|Name|Der Name des Konnektors.|Aktueller Name|  
|Namespace|Der Namespace, der diesen Connector verbunden ist.|Aktueller Namespace|  
|QuickInfo\-Typ|Wie die QuickInfo definiert ist \(korrigiert, Variablen oder keine\).  Wenn er korrigiert, und anschließend wird, wird der Wert der `Fixed Tooltip Text`\-Eigenschaft als QuickInfo verwendet. Variablen\-, wenn die QuickInfo dann im benutzerdefinierten Code definiert ist.|\<Keine\>|  
|Hinweise|Informelle Hinweise, die diesem Konnektor zugeordnet sind.|\<Keine\>|  
|Routing\-Format|Die Formatvorlage, die zum Weiterleiten des Konnektors verwendet wird.  Ein `Rectilinear` Konnektor führt nach Bedarf rechtwinklig gedreht wird. `Straight` ein Konnektor, jedoch nicht.|Geradlinig|  
|Farbe als Eigenschaft verfügbar gemachte<br /><br /> Bindestrich\-Format als Eigenschaft verfügbar gemachte<br /><br /> Stärke als Eigenschaft verfügbar gemachte<br /><br /> Exposee\-Textfarbe|Wenn `True`, der Benutzer die angegebene Eigenschaft ein Formular festlegen kann.  Wenn Sie dies mit der rechten Maustaste auf die Form, und klicken Sie auf Definition **Verfügbar gemacht hinzufügen**festlegen.|False|  
|Beschreibung|Ein Dokument den generierten Designer verwenden.|\<Keine\>|  
|Angezeigter Name|Der Name, der im generierten Designer für den Konnektor angezeigt wird.|\<Keine\>|  
|Fester QuickInfo\-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<Keine\>|  
|Hilfeschlüsselwort|Das Schlüsselwort, das dem Index F1\-Hilfe für dieses Element verwendet wird.|\<Keine\>|  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)