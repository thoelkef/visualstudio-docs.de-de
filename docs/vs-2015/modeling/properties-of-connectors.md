---
title: Eigenschaften von Konnektoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e2a0dbf1570e8a1ba29c82f1e492b9cc6852cccb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524312"
---
# <a name="properties-of-connectors"></a>Eigenschaften von Konnektoren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Eigenschaften von Connectors](https://docs.microsoft.com/visualstudio/modeling/properties-of-connectors).  
  
Verbinder repräsentieren domänenbeziehungen in einen generierten Designer.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md). Weitere Informationen zum Verwenden dieser Eigenschaften finden Sie unter [anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Connectors verfügen über die Eigenschaften, die in der folgenden Tabelle aufgeführt sind.  
  
|Eigenschaft|Beschreibung|Standard|  
|--------------|-----------------|-------------|  
|Farbe|Die Farbe dieses Verbinders.|Schwarz|  
|Dash-Format|Der Strichstil für die Zeile für diesen Connector (einfarbig, Bindestrich, Punkt, DashDot, Strich oder Benutzerdefiniert).|Basis|  
|Quellendlinienstärke|Die quellendlinienstärke für diesen Connector (HollowArrow EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond oder keine).|Keiner|  
|Zielendlinienart|Die zielendlinienart für diesen Connector (HollowArrow EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond oder keine).|Keiner|  
|Textfarbe|Die Farbe, die für Text-Decorators verwendet wird, die mit diesem Connector verknüpft sind.|Schwarz|  
|Stärke|Die Stärke der Linie für dieses Verbinders, gemessen in Zoll.|0.03125|  
|Zugriffsmodifizierer|Die Zugriffsebene der Klasse (`public` oder `internal`).|Public|  
|Benutzerdefinierte Attribute|Verwendet, um die Attribute der Quellklasse Code hinzufügen, die von diesem Connector generiert wird.|\<Keine >|  
|Double-Wert generiert abgeleitet|Wenn `True`, sowohl eine Basisklasse und eine partielle Klasse (zur Unterstützung von Anpassung über überschreibungen) generiert werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Hat benutzerdefinierten Konstruktor|Wenn `True`, ein benutzerdefinierter Konstruktor wird im Quellcode angegeben werden. Weitere Informationen finden Sie unter [überschreiben und Erweitern der generierten Klassen](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Vererbungsmodifizierer|Beschreibt die Art der Vererbung, der die Quellklasse in der Code ein, die vom Connector generiert wird (`none`, `abstract` oder `sealed`).|Keine|  
|Basisverbinder|Die Basisklasse dieses Verbinders.|(keine)|  
|name|Der Name dieses Verbinders.|Aktuelle name|  
|Namespace|Der Namespace, der diesen Connector zugeordnet ist.|Aktuellen namespace|  
|QuickInfo-Typ|Wie die QuickInfo definiert ist (fest, Variable oder keine). Wenn fest, klicken Sie dann den Wert des der `Fixed Tooltip Text` Eigenschaft wird als QuickInfo verwendet, wenn die Variable, klicken Sie dann die QuickInfo wird im benutzerdefinierten Code definiert.|\<Keine >|  
|Hinweise|Informelle Hinweise, die mit diesem Connector verknüpft sind.|\<Keine >|  
|Routingstil|Der Stil, der für das routing des Connectors verwendet wird. Ein `Rectilinear` Connector stellt Rechtwinklige Durchgängen erforderlich; eine `Straight` Verbinder nicht.|Pfeilspitzentypen zur Verfügung stehen|  
|Verfügbar gemachte Farbe als Eigenschaft<br /><br /> Als Eigenschaft verfügbar gemachte Strichstil<br /><br /> Die Stärke als Eigenschaft verfügbar gemacht<br /><br /> Stellt Text Color|Wenn `True`, der Benutzer kann die angegebene Eigenschaft einer Form festlegen. Um dies festzulegen, mit der rechten Maustaste in der Definition der Form, und klicken Sie auf **verfügbare hinzufügen**.|False|  
|Beschreibung|Dokumentieren des generierten Designers verwendet.|\<Keine >|  
|Anzeigename|Der Name, der im generierten Designer für diesen Connector angezeigt wird.|\<Keine >|  
|Feste QuickInfo-Text|Der Text, der für eine feste QuickInfo verwendet wird.|\<Keine >|  
|Hilfsschlüsselwort|Das Schlüsselwort, das zum Indizieren der F1-Hilfe für dieses Element verwendet wird.|\<Keine >|  
  
## <a name="see-also"></a>Siehe auch  
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



