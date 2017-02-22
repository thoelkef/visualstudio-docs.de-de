---
title: "Eigenschaften von Decorators | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Decorators"
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 23
caps.handback.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Eigenschaften von Decorators
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Decorator\-Elemente sind, Symbole oder simsen Erweitern\/Reduzieren chevrone, die Formen oder Konnektoren im Diagramm angezeigt werden können.  In den folgenden Tabellen sind die Eigenschaften für die drei Arten des Decorator\-Elements an.  Einige Eigenschaften werden nur in Form decorator\-elementen oder nur auf Konnektor decorator\-elementen.  
  
 Weitere Informationen finden Sie unter [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md).  Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)verwendet.  
  
## Erweitert\/Einsturz\-Decorator\-Element  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|DisplayName|Der Name des Decorator\-Elements, das im generierten Designer angezeigt wird.|Erweitern Sie Einsturz\-Decorator\-Element|  
|Name|Der Name des Decorator\-Elements.|ExpandCollapseDecorator|  
|Hinweise|Informelle Hinweise, die diesem Decorator\-Element zugeordnet sind.|\<Keine\>|  
|HorizontalOffset|Der horizontale Offset in Bezug auf die Standardposition des Decorator\-Elements, in Zoll.  \(nur auf Formen.\)|0|  
|VerticalOffset|Der vertikale Offset in Bezug auf die Standardposition des Decorator\-Elements, in Zoll.  \(nur auf Formen.\)|0|  
|OffsetFromLine|Der Offset des Decorator\-Elements aus der Zeile in Bezug zu seiner Standardposition, in Zoll.  \(nur auf Verbindungen.\)|0|  
|OffsetFromShape|Der Offset des Decorator\-Elements von der Form, relativ zu dessen Standardposition, in Zoll.  \(nur auf Verbindungen.\)|0|  
|Position|Die Standardposition des Decorator\-Elements.|SourceTop|  
  
## Symbol\-Decorator\-Element  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|DefaultIcon|Der Pfad des anzuzeigenden Symbols oder der Bilddatei.|\<Keine\>|  
|DisplayName|Der Name des generierten im Designer angezeigt werden soll, Decorator\-Elements.|Symbol\-Decorator\-Element|  
|Name|Der Name des Decorator\-Elements.|IconDecorator|  
|Hinweise|Informelle Hinweise, die mit dem Decorator\-Element zugeordnet sind.|\<Keine\>|  
|HorizontalOffset|Der horizontale Offset in Bezug auf die Standardposition des Decorator\-Elements, in Zoll.  \(nur auf Formen.\)|0|  
|VerticalOffset|Der vertikale Offset in Bezug auf die Standardposition des Decorator\-Elements, in Zoll.  \(nur auf Formen.\)|0|  
|OffsetFromLine|Der Offset des Decorator\-Elements aus der Zeile in Bezug zu seiner Standardposition, in Zoll.  \(nur auf Verbindungen.\)|0|  
|OffsetFromShape|Der Offset des Decorator\-Elements von der Form, relativ zu dessen Standardposition, in Zoll.  \(nur auf Verbindungen.\)|0|  
|Position|Die Standardposition des Decorator\-Elements.|SourceTop|  
  
## TextDecorator  
  
|Property|Beschreibung|Standardwert|  
|--------------|------------------|------------------|  
|DefaultText|Der Standardtext angezeigt werden soll.|Bezeichnung|  
|DisplayName|Der Name des generierten im Designer angezeigt werden soll, Decorator\-Elements.|Bezeichnung|  
|FontSize|Der Schriftgrad für den Text, der im Decorator\-Element angezeigt wird.|8|  
|FontStyle|Der Schriftschnitt für den Text, der im Decorator\-Element angezeigt wird.|Regulär|  
|Name|Der Name des Decorator\-Elements.|Bezeichnung|  
|Hinweise|Informelle Hinweise, die mit dem Decorator\-Element zugeordnet sind.|\<Keine\>|  
|HorizontalOffset|Der horizontale Offset in Bezug auf die Standardposition des Decorator\-Elements, in Zoll.  \(nur auf Formen.\)|0|  
|VerticalOffset|Der vertikale Offset in Bezug auf die Standardposition des Decorator\-Elements, in Zoll.  \(nur auf Formen.\)|0|  
|OffsetFromLine|Der Offset des Decorator\-Elements aus der Zeile in Bezug zu seiner Standardposition, in Zoll.  \(nur auf Verbindungen.\)|0|  
|OffsetFromShape|Der Offset des Decorator\-Elements von der Form, relativ zu dessen Standardposition, in Zoll.  \(nur auf Verbindungen.\)|0|  
|Position|Die Standardposition des Decorator\-Elements.|TargetBottom|  
  
## Siehe auch  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/de-de/ca5e84cb-a315-465c-be24-76aa3df276aa)