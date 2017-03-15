---
title: "Konstante Knoten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c798a50-a2d7-459b-9879-ad4ad8290c9b
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# Konstante Knoten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Shader\-Designer stellen konstante Knoten Literalwerte und interpolierte Vertexattribute bei Pixel\-Shader\-Berechnungen dar.  Da Vertexattribute interpoliert werden, und daher bei jedem Pixel unterschiedlich ausfallen, empfängt jede Pixel\-Shader\-Instanz eine andere Version der Konstante.  Dadurch erfährt jedes Pixel eine individuelles Darstellung.  
  
## Interpolation von Vertexattributen  
 Das Bild einer 3D\-Szene in einem Spiel oder einer App wird erzeugt, indem eine Anzahl von Objekten mathematisch in Pixel auf dem Bildschirm transformiert werden. Die Objekte werden über Vertices, Vertextattribute und primitive Definition definiert.  Alle erforderlichen Informationen zur individuellen Darstellung eines Pixels, werden durch Vertexattribute angegeben. Diese werden entsprechend der Nähe des Pixels zu den verschiedenen Vertices gemischt, die sein *Primitiv* bilden.  Bei einer Primitive handelt es sich um ein grundlegendes Renderingelement; das heißt, eine einfache Form wie einen Punkt, eine Zeile oder ein Dreieck.  Ein Pixel, das nur nahe bei einem Vertex liegt, erhält Konstanten, die mit diesem Vertex fast identisch sind. Ein Pixel, dessen Abstand zu allen Vertices einer Primitive gleichmäßig ist, erhält Konstanten, die dem Durchschnitt dieser Vertices entsprechen.  In der Grafikprogrammierung gelten die von den Pixeln empfangen Konstanten als *interpoliert*.  Pixeln auf diese Weise Konstantendaten bereitzustellen, führt zu sehr guter visueller Qualität und reduziert gleichzeitig Speicherbedarf\- und Bandbreitenanforderungen.  
  
 Obwohl jede Pixel\-Shader\-Instanz nur einen Satz Konstantenwerte erhält und diese Werte nicht geändert werden können, erhalten unterschiedliche Pixel\-Shader\-Instanzen verschiedene Konstantendatensätze.  Dieser Entwurf ermöglicht einem Shaderprogramm, für jedes Pixel in der Primitive eine andere Farbeausgabe zu erzeugen.  
  
## Konstantenknotenverweis  
  
|Knoten|Details|Eigenschaften|  
|------------|-------------|-------------------|  
|**Kameravektor**|Der Vektor, der sich vom aktuellen Pixel bis zur Kamera im Raum erstreckt.<br /><br /> Damit können Sie Reflexionen im Raum berechnen.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float3`<br /> Der Vektor vom aktuellen Pixel zur Kamera.|Kein|  
|**Farbkonstante**|Ein konstanter Farbwert.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float4`<br /> Der Farbwert.|**Ausgabe**<br /> Der Farbwert.|  
|**Konstante**|Ein konstanter Skalarwert.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float`<br /> Der Skalarwert.|**Ausgabe**<br /> Der Skalarwert.|  
|**2D\-Konstante**|Eine Vektorkonstante aus zwei Komponenten.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float2`<br /> Der Vektorwert.|**Ausgabe**<br /> Der Vektorwert.|  
|**3D\-Konstante**|Eine Vektorkonstante aus drei Komponenten.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float3`<br /> Der Vektorwert.|**Ausgabe**<br /> Der Vektorwert.|  
|**4D\-Konstante**|Eine Vektorkonstante aus vier Komponenten.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float4`<br /> Der Farbwert.|**Ausgabe**<br /> Der Vektorwert.|  
|**Normalisierte Position**|Die Position des aktuellen Pixels, ausgedrückt in normalisierten Gerätekoordinaten.<br /><br /> Die x\-Koordinate und die y\-Koordinate verfügen über Werte in einem Bereich von \[– 1, 1\]. Der Wert der z\-Koordinate liegt in einem Bereich von \[0, 1\], und die w\-Komponente enthält den Punkttiefenwert im Ansichtsraum. W wird nicht normalisiert.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float4`<br /> Die Position des aktuellen Pixels.|Kein|  
|**Punktfarbe**|Die diffuse Farbe des aktuellen Pixels. Eine Kombination aus der diffusen Farbe des Materials und den Farbattributen des Vertex.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float4`<br /> Die diffuse Farbe des aktuellen Pixels.|Kein|  
|**Punkttiefe**|Die Tiefe des aktuellen Pixels im Ansichtsraum.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float`<br /> Die Tiefe des aktuellen Pixels.|Kein|  
|**Normalisierte Punkttiefe**|Die Tiefe des aktuellen Pixels, ausgedrückt in normalisierten Gerätekoordinaten.<br /><br /> Das Ergebnis weist einen Wert im Bereich von \[0, 1\] auf.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float`<br /> Die Tiefe des aktuellen Pixels.|Kein|  
|**Bildschirmposition**|Die Position des aktuellen Pixels, ausgedrückt in Bildschirmkoordinaten.<br /><br /> Die Bildschirmkoordinaten basieren auf dem aktuellen Viewport.  Die x\- und y\-Komponenten enthalten die Bildschirmkoordinaten, die z\-Komponente enthält die Tiefe, die auf einen Bereich von \[0, 1\] normalisiert ist, und die w\-Komponente enthält den Tiefenwert im Ansichtsraum.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float4`<br /> Die Position des aktuellen Pixels.|Kein|  
|**Oberflächennormale**|Die Oberflächennormale des aktuellen Pixels im Objektraum.<br /><br /> Damit können Sie Beleuchtungseinwirkungen und Reflexionen im Objektraum berechnen.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float3`<br /> Die Oberflächennormale des aktuellen Pixels.|Kein|  
|**Kameravektor im Tangentialraum**|Der Vektor, der sich vom aktuellen Pixel bis zur Kamera im Tangentialraum erstreckt.<br /><br /> Damit können Sie Reflexionen im Tangentialraum berechnen.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float3`<br /> Der Vektor vom aktuellen Pixel zur Kamera.|Kein|  
|**Lichtrichtung im Tangentialraum**|Der Vektor, der die Richtung definiert, in der Licht von einer Lichtquelle im Tangentialraum des aktuellen Pixels umgewandelt wird.<br /><br /> Damit können Sie Beleuchtungs\- und Glanzeinwirkungen im Tangentialraum berechnen.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float3`<br /> Der Vektor vom aktuellen Pixel zu einer Lichtquelle.|Kein|  
|**World\-Normale**|Die Oberflächennormale des aktuellen Pixels im Raum.<br /><br /> Damit können Sie Beleuchtungseinwirkungen und Reflexionen im Raum berechnen.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float3`<br /> Die Oberflächennormale des aktuellen Pixels.|Kein|  
|**World\-Position**|Die Position des aktuellen Pixels im Raum.<br /><br /> **Ausgabe**<br /><br /> `Output`: `float4`<br /> Die Position des aktuellen Pixels.|Kein|