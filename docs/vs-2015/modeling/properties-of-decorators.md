---
title: Eigenschaften von Decorators | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dc111cf868d2136a4d274889d96d50d2c9500a9a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523727"
---
# <a name="properties-of-decorators"></a>Eigenschaften von Decorators
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Eigenschaften-Decorator-Elemente](https://docs.microsoft.com/visualstudio/modeling/properties-of-decorators).  
  
Decorator-Elemente sind Symbole, Text oder Chevrons erweitern/reduzieren, die Formen oder Konnektoren im Diagramm angezeigt werden können. Die folgenden Tabellen zeigen die Eigenschaften für die drei Arten von Decorator-Element. Einige Eigenschaften werden nur auf das Form-Decorator-Elemente oder nur auf die Connector-Decorator-Elemente angezeigt.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Erweitern/Reduzieren-Decorator-Element  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|DisplayName|Der Name des Decorator-Elements, der im generierten Designer angezeigt wird.|Erweitern Reduzieren-Decorator-Element|  
|name|Der Name des Decorator-Elements.|ExpandCollapseDecorator|  
|Hinweise|Informelle Hinweise, die dieses Decorator-Element zugeordnet sind.|\<Keine >|  
|HorizontalOffset|Der horizontale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|OffsetFromLine|Der Offset des Decorator-Elements über die Befehlszeile, relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|OffsetFromShape|Der Offset des Decorator-Elements aus der Form relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|Position|Die Standardposition des Decorator-Elements.|SourceTop|  
  
## <a name="icon-decorator"></a>Symbol für Decorator-Element  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|DefaultIcon-Werts|Der Pfad der Datei Symbol oder Bild, die angezeigt werden soll.|\<Keine >|  
|DisplayName|Der Name des Decorator-Elements, der im generierten Designer angezeigt werden.|Symbol für Decorator-Element|  
|name|Der Name des Decorator-Elements.|IconDecorator|  
|Hinweise|Informelle Hinweise, die das Decorator-Element zugeordnet sind.|\<Keine >|  
|HorizontalOffset|Der horizontale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|OffsetFromLine|Der Offset des Decorator-Elements über die Befehlszeile, relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|OffsetFromShape|Der Offset des Decorator-Elements aus der Form relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|Position|Die Standardposition des Decorator-Elements.|SourceTop|  
  
## <a name="textdecorator"></a>TextDecorator  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|DefaultText|Der Standardtext, der angezeigt werden.|Bezeichnung|  
|DisplayName|Der Name des Decorator-Elements, der im generierten Designer angezeigt werden.|Bezeichnung|  
|FontSize|Der Schriftgrad für den Text, der im Decorator-Element angezeigt wird.|8|  
|FontStyle|Der Schriftschnitt für den Text, der im Decorator-Element angezeigt wird.|Regulär|  
|name|Der Name des Decorator-Elements.|Bezeichnung|  
|Hinweise|Informelle Hinweise, die das Decorator-Element zugeordnet sind.|\<Keine >|  
|HorizontalOffset|Der horizontale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|OffsetFromLine|Der Offset des Decorator-Elements über die Befehlszeile, relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|OffsetFromShape|Der Offset des Decorator-Elements aus der Form relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|Position|Die Standardposition des Decorator-Elements.|TargetBottom|  
  
## <a name="see-also"></a>Siehe auch  
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



