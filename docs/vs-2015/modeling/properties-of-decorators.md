---
title: Eigenschaften von Decorators | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d9cd07ed41e39c931e67f43f1c77ff8bd56b2eb3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701777"
---
# <a name="properties-of-decorators"></a>Eigenschaften von Decorators
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Decorator-Elemente sind Symbole, Text oder Chevrons erweitern/reduzieren, die Formen oder Konnektoren im Diagramm angezeigt werden können. Die folgenden Tabellen zeigen die Eigenschaften für die drei Arten von Decorator-Element. Einige Eigenschaften werden nur auf das Form-Decorator-Elemente oder nur auf die Connector-Decorator-Elemente angezeigt.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## <a name="expandcollapse-decorator"></a>Erweitern/Reduzieren-Decorator-Element  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|DisplayName|Der Name des Decorator-Elements, der im generierten Designer angezeigt wird.|Erweitern Reduzieren-Decorator-Element|  
|Name|Der Name des Decorator-Elements.|ExpandCollapseDecorator|  
|Hinweise|Informelle Hinweise, die dieses Decorator-Element zugeordnet sind.|\<none>|  
|HorizontalOffset|Der horizontale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|OffsetFromLine|Der Offset des Decorator-Elements über die Befehlszeile, relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|OffsetFromShape|Der Offset des Decorator-Elements aus der Form relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|Position|Die Standardposition des Decorator-Elements.|SourceTop|  
  
## <a name="icon-decorator"></a>Symbol für Decorator-Element  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|DefaultIcon|Der Pfad der Datei Symbol oder Bild, die angezeigt werden soll.|\<none>|  
|DisplayName|Der Name des Decorator-Elements, der im generierten Designer angezeigt werden.|Symbol für Decorator-Element|  
|Name|Der Name des Decorator-Elements.|IconDecorator|  
|Hinweise|Informelle Hinweise, die das Decorator-Element zugeordnet sind.|\<none>|  
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
|Name|Der Name des Decorator-Elements.|Bezeichnung|  
|Hinweise|Informelle Hinweise, die das Decorator-Element zugeordnet sind.|\<none>|  
|HorizontalOffset|Der horizontale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-Elements, in Zoll. (Auf nur-Shapes.)|0|  
|OffsetFromLine|Der Offset des Decorator-Elements über die Befehlszeile, relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|OffsetFromShape|Der Offset des Decorator-Elements aus der Form relativ zur Standardposition in Zoll. (Auf Connectors nur.)|0|  
|Position|Die Standardposition des Decorator-Elements.|TargetBottom|  
  
## <a name="see-also"></a>Siehe auch  
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
