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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb837c9b3d465d229f64fac08dac02af8d50f5fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652015"
---
# <a name="properties-of-decorators"></a>Eigenschaften von Decorators
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Decoratoren sind Symbole, Text oder Erweiterungs-/reduzierungschevd, die auf Formen oder Connectors im Diagramm angezeigt werden können. Die folgenden Tabellen zeigen die Eigenschaften für die drei Arten von Decorator-Objekten. Einige Eigenschaften werden nur in Form-Decorator oder nur in Connector-Decorator-Zeichen angezeigt.

 Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Decorator erweitern/reduzieren

|Eigenschaft|BESCHREIBUNG|Standard|
|--------------|-----------------|-------------|
|DisplayName|Der Name des Decorators, der im generierten Designer angezeigt wird.|Erweitern des aufklappen-Decorators|
|Name|Der Name des Decorators.|ExpandCollapseDecorator|
|Hinweise|Informelle Notizen, die diesem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|SourceTop|

## <a name="icon-decorator"></a>Symboldecorator

|Eigenschaft|BESCHREIBUNG|Standard|
|--------------|-----------------|-------------|
|DefaultIcon|Der Pfad der Symbol-oder Bilddatei, die angezeigt werden soll.|\<none>|
|DisplayName|Der Name des Decorator-Designers, der im generierten Designer angezeigt werden soll.|Symboldecorator|
|Name|Der Name des Decorators.|IconDecorator|
|Hinweise|Informelle Notizen, die dem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Eigenschaft|BESCHREIBUNG|Standard|
|--------------|-----------------|-------------|
|DefaultText|Der Standardtext, der angezeigt werden soll.|Bezeichnung|
|DisplayName|Der Name des Decorator-Designers, der im generierten Designer angezeigt werden soll.|Bezeichnung|
|FontSize|Der Schrift Grad für den Text, der im Decorator angezeigt wird.|8|
|FontStyle|Der Schriftart Stil für den Text, der im Decorator angezeigt wird.|Regulär|
|Name|Der Name des Decorators.|Bezeichnung|
|Hinweise|Informelle Notizen, die dem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|TargetBottom|

## <a name="see-also"></a>Weitere Informationen
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
