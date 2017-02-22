---
title: "Texturknoten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: 12
caps.handback.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Texturknoten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Shader\-Designer dienen Texturknoten der Stichprobenahme für verschiedene Texturtypen und Geometrien und erzeugen oder transformieren Texturkoordinaten.  Texturen liefern Farb\- und Beleuchtungsdetails für Objekte.  
  
## Übersicht über Texturknoten  
  
|Knoten|Details|Eigenschaften|  
|------------|-------------|-------------------|  
|**Cubemap\-Sample**|Nimmt an den angegebenen Koordinaten eine Farbstichprobe aus einer Cubemap.<br /><br /> Sie können eine Cubemap verwenden, um Farbdetails für Reflexionseffekte bereitzustellen oder um Texturen auf ein kugelförmiges Objekt anzuwenden und dabei weniger Verzerrung als bei einer 2D\-Textur zu erzielen.<br /><br /> **Eingabe:**<br /><br /> `UVW`: `float3`<br /> Ein Vektor, mit dem die Position auf dem Texturwürfel angegeben wird, an der die Stichprobe genommen wird.  Die Stichprobe wird an der Stelle genommen, an der dieser Vektor den Würfel schneidet.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Die Farbstichprobe.|**Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist.|  
|**Normalmap\-Sample**|Nimmt an den angegebenen Koordinaten eine Normalstichprobe aus einer 2D\-Normalmap.<br /><br /> Mit einer Normalmap können Sie die Darstellung zusätzlicher geometrischer Details auf der Oberfläche eines Objekts simulieren.  Normalmaps enthalten gepackte Daten, die einen Einheitsvektor anstelle von Farbdaten repräsentieren.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten, an denen die Stichprobe genommen wurde.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float3`<br /> Die Normalstichprobe.|**Achsenanpassung**<br /> Der Faktor zum Anpassen der Händigkeit des Normalmap\-Samples.<br /><br /> **Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist.|  
|**Schwenken\-UV**|Schwenkt die angegebenen Texturkoordinaten als Zeitfunktion.<br /><br /> Damit können Sie eine Textur\- oder Normalmap über die Oberfläche eines Objekts verschieben.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die zu schwenkenden Koordinaten.<br /><br /> `Time`: `float`<br /> Die in Sekunden\), von zu schwenkenden Zeitspanne.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Die geschwenkten Koordinaten.|**Geschwindigkeit X**<br /> Die Anzahl von Texeln, die pro Sekunde entlang der X\-Achse verschoben werden.<br /><br /> **Geschwindigkeit Y**<br /> Die Anzahl von Texeln, die pro Sekunde entlang der Y\-Achse verschoben werden.|  
|**Parallaxen\-UV**|Verschiebt die angegebenen Texturkoordinaten als Höhen\- und Blickwinkelfunktion.<br /><br /> Der Effekt wird als *Parallaxenmapping* oder virtuelles Verschiebungsmapping bezeichnet.  Damit können Sie eine Illusion von Tiefe auf einer flachen Oberfläche erzeugen.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die zu verschiebenden Koordinaten.<br /><br /> `Height`: `float`<br /> Der heightmap\-Wert, der den `UV`\-Koordinaten zugeordnet ist.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Die verschobenen Koordinaten.|**Tiefenebene**<br /> Die Referenztiefe für den Parallaxeneffekt.  Der Standardwert ist 0,5.  Kleinere Werte heben die Textur an, größere Werte senken sie auf die Oberfläche.<br /><br /> **Tiefenskala**<br /> Die Skala des Parallaxeneffektes.  Dadurch wird die offensichtliche Tiefe mehr oder weniger betont.  Typische Werte reichen von 0,02 bis 0,1.|  
|**Drehen\-UV**|Dreht die angegebenen Texturkoordinaten als Zeitfunktion um einen zentralen Punkt.<br /><br /> Damit können Sie eine Textur\- oder Normalmap auf der Oberfläche eines Objekts rotieren.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die zu drehenden Koordinaten.<br /><br /> `Time`: `float`<br /> Die in Sekunden\), von zu schwenkenden Zeitspanne.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Die gedrehten Koordinaten.|**X zentrieren**<br /> Die X\-Koordinate, die den Mittelpunkt der Drehung definiert.<br /><br /> **Y zentrieren**<br /> Die Y\-Koordinate, die den Mittelpunkt der Drehung definiert.<br /><br /> **Geschwindigkeit**<br /> Der Winkel im Bogenmaß, in dem sich die Textur pro Sekunde dreht.|  
|**Texturkoordinate**|Die Texturkoordinaten des aktuellen Pixels.<br /><br /> Die Texturkoordinaten werden durch Interpolieren der Texturkoordinatenattribute von benachbarten Vertices ermittelt.  Sie können sich dies als Position des aktuellen Pixels im Texturraum vorstellen.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Die Texturkoordinaten.|Kein|  
|**Texturdimensionen**|Gibt die Breite und Höhe einer 2D\-Texturmap aus.<br /><br /> Sie können die Texturdimensionen verwenden, um die Höhe und Breite der Textur in einem Shader zu berücksichtigen.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Die Breite und Höhe der Textur, ausgedrückt als Vektor.  Die Breite wird im ersten Element des Vektors gespeichert.  Die Höhe wird im zweiten Element gespeichert.|**Textur**<br /> Das Texturregister, das mit der Textur zugeordnet wird, dimensioniert.|  
|**Texeldelta**|Gibt das Delta \(Abstand\) zwischen den Texeln einer 2D\-Texturmap aus.<br /><br /> Sie können das Texeldelta verwenden, um nebeneinander liegende Texelwerte in einem Shader zu überprüfen.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float2`<br /> Das Delta \(Abstand\) eines Texel folgendermaßen Texel \(diagonal Scrollen in die positive Richtung\), ausgedrückt als Vektor in normalisiertem Texturraum vorstellen.  Sie können die Positionen aller benachbarten Texel berechnen, indem Sie selektiv die U\- oder v\-Koordinaten des Deltas ignorieren oder negierende.|**Textur**<br /> Das Texturregister, das dem Texeldelta zugeordnet ist.|  
|**Texturbeispiel**|Nimmt an den angegebenen Koordinaten eine Farbstichprobe aus einer 2D\-Texturmap.<br /><br /> Mit einer Texturmap können Sie Farbdetails auf der Oberfläche eines Objekts bereitstellen.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten, an denen die Stichprobe genommen wurde.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Die Farbstichprobe.|**Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist.|