---
title: Eigenschaften von Decorators
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14965f829530ba5a2f6a7797291e9d1cfab0ae2d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810053"
---
# <a name="properties-of-decorators"></a>Eigenschaften von Decorators
Decoratoren sind Symbole, Text oder Erweiterungs-/reduzierungschevd, die auf Formen oder Connectors im Diagramm angezeigt werden können. Die folgenden Tabellen zeigen die Eigenschaften für die drei Arten von Decorator-Objekten. Einige Eigenschaften werden nur in Form-Decorator oder nur in Connector-Decorator-Zeichen angezeigt.

 Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Decorator erweitern/reduzieren

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|DisplayName|Der Name des Decorators, der im generierten Designer angezeigt wird.|Erweitern des aufklappen-Decorators|
|name|Der Name des Decorators.|ExpandCollapseDecorator|
|Hinweise|Informelle Notizen, die diesem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|SourceTop|

## <a name="icon-decorator"></a>Symboldecorator

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|DefaultIcon|Der Pfad der Symbol-oder Bilddatei, die angezeigt werden soll.|\<none>|
|DisplayName|Der Name des Decorator-Designers, der im generierten Designer angezeigt werden soll.|Symboldecorator|
|name|Der Name des Decorators.|IconDecorator|
|Hinweise|Informelle Notizen, die dem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Eigenschaft|Beschreibung|Standard|
|-|-|-|
|DefaultText|Der Standardtext, der angezeigt werden soll.|Bezeichnung|
|DisplayName|Der Name des Decorator-Designers, der im generierten Designer angezeigt werden soll.|Bezeichnung|
|FontSize|Der Schrift Grad für den Text, der im Decorator angezeigt wird.|8|
|FontStyle|Der Schriftart Stil für den Text, der im Decorator angezeigt wird.|Regulär|
|name|Der Name des Decorators.|Bezeichnung|
|Hinweise|Informelle Notizen, die dem Decorator zugeordnet sind.|\<none>|
|Horizontal Offset|Der horizontale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|VerticalOffset|Der vertikale Offset relativ zur Standardposition des Decorator-in Zoll. (Nur bei Formen)|0|
|Offsetfromline|Der Offset des Decorators von der Linie relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Offsetfromshape|Der Offset des Decorator-Konstruktors von der Form relativ zu seiner Standardposition in Zoll. (Nur für Connectors.)|0|
|Position|Die Standardposition des Decorator-Konstruktors.|TargetBottom|

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](/previous-versions/bb126564(v=vs.100))