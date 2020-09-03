---
title: Eigenschaften von Connectors | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ea629e504c3ba74d35f3ad8aa89bc22cfae30df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652044"
---
# <a name="properties-of-connectors"></a>Eigenschaften von Konnektoren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Connectors stellen Domänen Beziehungen in einem generierten Designer dar.

 Weitere Informationen finden Sie unter [Definieren einer domänenspezifischen Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zur Verwendung dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Connectors verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.

|Eigenschaft|BESCHREIBUNG|Standard|
|--------------|-----------------|-------------|
|„Color“ (Farbe)|Die Farbe dieses Verbindungs-.|Schwarz|
|Strich Stil|Der Strich Stil für die Linie für diesen Connector (Solid, Dash, dot, DashDot, DashDotDot oder Custom).|Basis|
|Quellend-Stil|Der Quellend Stil für diesen Connector (hollowarrow, emptypfeil, filledarrow, EmptyDiamond, FilledDiamond oder None).|Keine|
|Zielend-Stil|Der zielend-Stil für diesen Connector (hollowarrow, EmptyArrow, filledarrow, EmptyDiamond, FilledDiamond oder None).|Keine|
|Textfarbe|Die Farbe, die für Text-Decorator verwendet wird, die diesem Connector zugeordnet sind.|Schwarz|
|Stärke|Die Stärke der Linie für diesen Connector (gemessen in Zoll).|0,03125|
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse ( `public` oder `internal` ).|Öffentlich|
|Benutzerdefinierte Attribute|Wird verwendet, um der Quell Code Klasse Attribute hinzuzufügen, die von diesem Connector generiert werden.|\<none>|
|Generiert doppelte abgeleitete|Gibt `True` an, dass sowohl eine Basisklasse als auch eine partielle Klasse (zur Unterstützung der Anpassung durch über schreibungen) generiert werden. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Hat benutzerdefinierten Konstruktor|Gibt `True` an, dass ein benutzerdefinierter Konstruktor im Quellcode bereitgestellt wird. Weitere Informationen finden Sie unter Überschreiben [und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|Falsch|
|Vererbungs Modifizierer|Beschreibt die Art der Vererbung der Quell Code Klasse, die vom Connector generiert wird ( `none` `abstract` oder `sealed` ).|Keine|
|Basisconnector|Die Basisklasse dieses Verbindungs Punkts.|(none)|
|Name|Der Name dieses Connector.|Aktueller Name|
|Namespace|Der Namespace, der mit diesem Connector verbunden ist.|Aktueller Namespace|
|QuickInfo-Typ|Wie die QuickInfo definiert wird (Fixed, Variable oder None). Wenn Sie festgelegt ist, wird der Wert der `Fixed Tooltip Text` Eigenschaft als QuickInfo verwendet. wenn die Variable ist, wird die QuickInfo in benutzerdefiniertem Code definiert.|\<none>|
|Hinweise|Informelle Hinweise, die mit diesem Connector verknüpft sind.|\<none>|
|Routing Stil|Der Stil, der zum Weiterleiten des Verbindungs-Connector verwendet wird. Bei einem Connector werden nach `Rectilinear` Bedarf rechts gerichtete, bei einem `Straight` Connector vornimmt.|Rectilinear|
|Verfügbar gemachte Farbe als Eigenschaft<br /><br /> Verfügbar gemachte Bindestriche als Eigenschaft<br /><br /> Verfügbar gemachte Dicke als Eigenschaft<br /><br /> Macht Textfarbe verfügbar.|Wenn `True` der Wert ist, kann der Benutzer die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, klicken Sie mit der rechten Maustaste auf die Form Definition, und **Klicken Sie auf**verfügbar machen|Falsch|
|BESCHREIBUNG|Wird verwendet, um den generierten Designer zu dokumentieren.|\<none>|
|Anzeigename|Der Name, der im generierten Designer für diesen Connector angezeigt wird.|\<none>|
|Fester QuickInfo-Text|Der Text, der für eine fixierte QuickInfo verwendet wird.|\<none>|
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Element verwendet wird.|\<none>|

## <a name="see-also"></a>Weitere Informationen
 [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
