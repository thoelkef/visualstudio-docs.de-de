---
title: Texturknoten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bda107323b24940ed8cab18a61f9e491f8392f53
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252355"
---
# <a name="texture-nodes"></a>Texturknoten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im Shader Designer beproben Texturknoten verschiedene Texturtypen und Geometrien und erzeugen ider transformieren Texturkoordinaten. Texturen bieten Farb- und Beleuchtungsdetails auf Objekten.  
  
## <a name="texture-node-reference"></a>Übersicht über Texturknoten  
  
|Knoten|Details|Eigenschaften|  
|----------|-------------|----------------|  
|**Cubemap-Beispiel**|Entnimmt ein Farbsample aus einer Cubemap an den angegebenen Koordinaten.<br /><br /> Sie können mithilfe einer Cubemap Farbdetails für Reflexionseffekte bereitstellen oder Texturen auf ein kugelförmiges Objekt anwenden und dabei weniger Verzerrung als bei einer 2D-Textur erzielen.<br /><br /> **Eingabe:**<br /><br /> `UVW`: `float3`<br /> Ein Vektor, der die Position auf dem Texturcube, auf dem das Sample entnommen wurde. Das Sample wird am Schnittpunkt des Vektors mit dem Cube erfasst.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Farbbeispiel.|**Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist.|  
|**Normalmap-Sample**|Entnimmt ein Normalsample von einer 2D-Normalmap an den angegebenen Koordinaten<br /><br /> Sie können mit einer Normalmap die Darstellung der zusätzlichen geometrischen Details auf der Oberfläche eines Objekts simulieren. Normalmap enthalten gepackte Daten die einen Einheitsvektor anstelle von Farbdaten darstellen<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten, an denen das Sample entnommen wird.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float3`<br /> Normalsample|**Achsenanpassung**<br /> Der Faktor zum Anpassen der Händigkeit des Normalmap-Samples.<br /><br /> **Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist.|  
|**Schwenken-UV**|Schwenkt die angegebenen Texturkoordinaten in Abhängigkeit von der Zeit.<br /><br /> Damit können Sie eine Textur oder die Normalmap auf der Oberfläche eines Objekts verschieben.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Zu schwenkende Koordinaten<br /><br /> `Time`: `float`<br /> Die Zeitdauer in Sekunden des Schwenkvorgangs.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Geschwenkte Koordinaten|**Geschwindigkeit X**<br /> Die Anzahl von Texeln, die pro Sekunde entlang der X-Achse verschoben werden.<br /><br /> **Geschwindigkeit Y**<br /> Die Anzahl von Texeln, die pro Sekunde entlang der Y-Achse verschoben werden.|  
|**Parallaxen-UV**|Verschiebt die angegebenen Texturkoordinaten in Abhängigkeit von Höhe und Anzeigewinkel.<br /><br /> Der Effekt wird als *Parallaxenmapping* oder virtuelles Verschiebungsmapping bezeichnet. Damit können Sie Illusion von Tiefe auf einer flachen Oberfläche erzeugen.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Zu verschiebende Koordinaten<br /><br /> `Height`: `float`<br /> Der den `UV`-Koordinaten zugeordnete Heightmap-Wert.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Verschobene Koordinaten|**Tiefenebene**<br /> Referenztiefe für den Parallaxeneffekt. Der Standardwert ist 0,5. Kleinere Werte heben die Textur an; größere Werte, die senken sie auf die Oberfläche.<br /><br /> **Tiefenskala**<br /> Die Skalierung des Parallaceneffekts. Dadurch wird die optische Tiefe mehr oder weniger ausgeprägt. Die Werte stammen normalerweise auf dem Bereich von 0,02 bis 0,1.|  
|**Drehen-UV**|Dreht die angegebenen Texturkoordinaten in Abhängigkeit von der Zeit um einen Mittelpunkt.<br /><br /> Damit können Sie eine Textur oder die Normalmap auf der Oberfläche eines Objekts drehen.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Zu drehende Koordinaten<br /><br /> `Time`: `float`<br /> Die Zeitdauer in Sekunden des Schwenkvorgangs.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Gedrehte Koordinaten|**X zentrieren**<br /> Die X-Koordinate, die den Mittelpunkt der Drehung definiert.<br /><br /> **Y zentrieren**<br /> Die Y-Koordinate, die den Mittelpunkt der Drehung definiert.<br /><br /> **Geschwindigkeit**<br /> Der Winkel im Bogenmaß, in dem sich die Textur pro Sekunde dreht.|  
|**Texturkoordinate**|Die Texturkoordinaten des aktuellen Pixels.<br /><br /> Die Texturkoordinaten werden durch die Interpolation zwischen den Attributen der Texturkoordinatenattribute von benachbarten Scheitelpunkten bestimmt. Sie können sich dies als die Position des aktuellen Pixels im Texturraum vorstellen.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Texturkoordinaten|Keiner|  
|**Texturdimensionen**|Gibt die Breite und Höhe einer 2D-Texturmap aus.<br /><br /> Sie können die Texturdimensionen verwenden, um die Breite und Höhe der Textur in einem Shader zu berücksichtigen.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Die Breite und Höhe der Textur, ausgedrückt als Vektor. Die Breite wird als das erste Element des Vektors gespeichert. Die Höhe wird in das zweite Element gespeichert.|**Textur**<br /> Das Texturregister, das den Texturdimensionen zugeordnet ist.|  
|**Texeldelta**|Gibt das Delta (Abstand) zwischen den Texeln einer 2D-Texturmap aus.<br /><br /> Sie können mit dem Texeldelta benachbarte Texelwerte in einem Shader sampeln.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Das Delta (Abstand) von einem zum nächsten Texel (diagonal in positiver Richtung verschieben), ausgedrückt als Vektor im normalisierten Texturraum. Sie können die Positionen aller benachbarten Texel ableiten, indem Sie selektiv entweder die U- oder die V- Koordinate des Deltas ignorieren oder negieren.|**Textur**<br /> Das Texturregister, das dem Texel zugeordnet ist.|  
|**Texturbeispiel**|Entnimmt ein Farbsample aus einer 2D-Texturmap an den angegebenen Koordinaten.<br /><br /> Mit einer Texturmap können Sie Farbdetails auf der Oberfläche eines Objekts bereitstellen.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten, an denen das Sample entnommen wird.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Farbbeispiel.|**Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist.|



