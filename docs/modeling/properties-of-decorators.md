---
title: Eigenschaften des Decorators | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: "23"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 23288d1afe9b9c0a181a5d978b1956071b683218
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-decorators"></a>Eigenschaften von Decorators
Decorator-Elemente sind Symbole, Text oder erweitern/reduzieren in spitzen Klammern, die auf die Formen oder Verbindungen im Diagramm angezeigt werden können. In den folgenden Tabellen zeigen die Eigenschaften für die drei Arten von Decorator-Element. Einige der Eigenschaften werden nur auf die Form Decorator-Elemente oder nur auf Connector Decorator-Elementen angezeigt.  
  
 Weitere Informationen finden Sie unter [zum Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Expand/Collapse-Decorator-Element  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|DisplayName|Der Name des Decorator-Element, die im generierten-Designer angezeigt werden.|Erweitern Reduzieren Decorator-Element|  
|Name|Der Name des der Decorator-Element.|ExpandCollapseDecorator|  
|Hinweise|Informelle Hinweise, die diese Decorator-Element zugeordnet sind.|\<keine >|  
|HorizontalOffset|Der horizontale Offset relativ zum die Standardposition der Decorator in Zoll. (Auf nur-Shapes.)|0|  
|VerticalOffset|Der vertikale Offset relativ zum die Standardposition der Decorator in Zoll. (Auf nur-Shapes.)|0|  
|OffsetFromLine|Der Offset der Decorator-Element aus der Zeile, relativ zum Standardposition in Zoll. (Auf Connectors nur.)|0|  
|OffsetFromShape|Der Offset der Decorator-Element aus der Form relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|Position|Die Standardposition der Decorator.|SourceTop|  
  
## <a name="icon-decorator"></a>Symbol "Decorator-Element  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|DefaultIcon|Der Pfad der Datei Symbol oder Bild angezeigt werden.|\<keine >|  
|DisplayName|Der Name des der Decorator-Element in der generierten-Designer angezeigt werden.|Symbol "Decorator-Element|  
|Name|Der Name des der Decorator-Element.|IconDecorator|  
|Hinweise|Informelle Hinweise, die die Decorator-Element zugeordnet sind.|\<keine >|  
|HorizontalOffset|Der horizontale Offset relativ zum die Standardposition der Decorator in Zoll. (Auf nur-Shapes.)|0|  
|VerticalOffset|Der vertikale Offset relativ zum die Standardposition der Decorator in Zoll. (Auf nur-Shapes.)|0|  
|OffsetFromLine|Der Offset der Decorator-Element aus der Zeile, relativ zum Standardposition in Zoll. (Auf Connectors nur.)|0|  
|OffsetFromShape|Der Offset der Decorator-Element aus der Form relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|Position|Die Standardposition der Decorator.|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|DefaultText|Der Standardtext angezeigt werden.|Bezeichnung|  
|DisplayName|Der Name des der Decorator-Element in der generierten-Designer angezeigt werden.|Bezeichnung|  
|FontSize|Der Schriftgrad für den Text, der in der Decorator-Element angezeigt wird.|8|  
|FontStyle|Der Schriftschnitt für den Text, der in der Decorator-Element angezeigt wird.|Regulär|  
|Name|Der Name des der Decorator-Element.|Bezeichnung|  
|Hinweise|Informelle Hinweise, die die Decorator-Element zugeordnet sind.|\<keine >|  
|HorizontalOffset|Der horizontale Offset relativ zum die Standardposition der Decorator in Zoll. (Auf nur-Shapes.)|0|  
|VerticalOffset|Der vertikale Offset relativ zum die Standardposition der Decorator in Zoll. (Auf nur-Shapes.)|0|  
|OffsetFromLine|Der Offset der Decorator-Element aus der Zeile, relativ zum Standardposition in Zoll. (Auf Connectors nur.)|0|  
|OffsetFromShape|Der Offset der Decorator-Element aus der Form relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|Position|Die Standardposition der Decorator.|TargetBottom|  
  
## <a name="see-also"></a>Siehe auch  
 [Domänenspezifische Sprache Tools Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)