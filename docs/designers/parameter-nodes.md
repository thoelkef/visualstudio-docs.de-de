---
title: "Parameterknoten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da54db0b-3a3d-48dc-858c-7ac43aa04b13
caps.latest.revision: 10
caps.handback.revision: 10
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Parameterknoten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Shader\-Designer stellen Parameterknoten Eingaben für den Shader dar, die pro Zeichenvorgang von der App gesteuert werden, z. B. Materialeigenschaften, gerichtetes Licht, Kameraposition und Zeit.  Da diese Parameter bei jedem Zeichnen\-Aufruf geändert werden können, können Sie den gleichen Shader verwenden, um ein Objekt unterschiedlich darzustellen.  
  
## Parameterknotenverweis  
  
|Knoten|Details|Eigenschaften|  
|------------|-------------|-------------------|  
|**World\-Position \(Kamera\)**|Die Position der Kamera im Raum.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Position der Kamera.|Kein|  
|**Lichtrichtung**|Der Vektor, der die Richtung definiert, in der Licht von einer Lichtquelle im Raum umgewandelt wird.<br /><br /> Damit können Sie Beleuchtungs\- und Glanzeinwirkungen im Raum berechnen.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float3`<br /> Der Vektor vom aktuellen Pixel zu einer Lichtquelle.|Kein|  
|**Material Ambiente**|Die diffuse Farbeinwirkung des aktuellen Pixels aufgrund der indirekten Beleuchtung.<br /><br /> Die diffuse Farbe eines Pixels simuliert, wie die Beleuchtung mit groben Oberflächen interagiert.  Über den Parameter "Material \(Umgebung\)" können Sie ungefähr bestimmen, wie die indirekte Beleuchtung auf die Erscheinung eines Objekts in der realen Welt einwirkt.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Die diffuse Farbe des aktuellen Pixels aufgrund der indirekten Beleuchtung \(d. h. der Umgebung\).|**Zugriff**<br /> **Öffentlich**, damit die Eigenschaft im Modell\-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**<br /> Die diffuse Farbe des aktuellen Pixels aufgrund der indirekten Beleuchtung \(d. h. der Umgebung\).|  
|**Material Diffus**|Eine Farbe, die die Streuung der direkten Beleuchtung durch das aktuelle Pixel beschreibt.<br /><br /> Die diffuse Farbe eines Pixels simuliert, wie die Beleuchtung mit groben Oberflächen interagiert.  Über den Parameter "Material \(Diffus\)" können Sie ändern, wie das aktuelle Pixel direktes Licht, d. h. gerichtetes Licht, punktuelles Licht und Spotlights, verteilt.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Eine Farbe, die die Streuung der direkten Beleuchtung durch das aktuelle Pixel beschreibt.|**Zugriff**<br /> **Öffentlich**, damit die Eigenschaft im Modell\-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**<br /> Eine Farbe, die die Streuung der direkten Beleuchtung durch das aktuelle Pixel beschreibt.|  
|**Material Selbstleuchtend**|Die Farbeinwirkung des aktuellen Pixels aufgrund der Beleuchtung, die es für sich selbst erzeugt.<br /><br /> Damit können Sie ein glühendes Objekt simulieren, d. h. ein Objekt, das sich selbst mit Licht versorgt.  Dieses Licht wirkt sich nicht auf andere Objekte aus.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Die Farbeinbringung des aktuellen Pixels aufgrund der selbsterzeugten Beleuchtung.|**Zugriff**<br /> **Öffentlich**, damit die Eigenschaft im Modell\-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**<br /> Die Farbeinbringung des aktuellen Pixels aufgrund der selbsterzeugten Beleuchtung.|  
|**Material Glänzend**|Eine Farbe, die die Reflexion der direkten Beleuchtung durch das aktuelle Pixel beschreibt.<br /><br /> Die glänzende Farbe eines Pixels simuliert, wie die Beleuchtung mit glatten, spiegelähnlichen Oberflächen interagiert.  Über den Parameter "Material \(Glanz\)" können Sie ändern, wie das aktuelle Pixel direktes Licht, d. h. gerichtetes Licht, punktuelles Licht und Spotlights, reflektiert.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Eine Farbe, die die Reflexion der direkten Beleuchtung durch das aktuelle Pixel beschreibt.|**Zugriff**<br /> **Öffentlich**, damit die Eigenschaft im Modell\-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**<br /> Eine Farbe, die die Reflexion der direkten Beleuchtung durch das aktuelle Pixel beschreibt.|  
|**Material Glanzkraft**|Ein Skalarwert, der die Intensität von Glanzlichtern beschreibt.<br /><br /> Je größer die Glanzkraft, desto intensiver und strahlender werden die Glanzlichter.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float`<br /> Der Exponent, mit dem die Intensität von Glanzlichtern auf dem aktuellen Pixels definiert wird.|**Zugriff**<br /> **Öffentlich**, damit die Eigenschaft im Modell\-Editor festgelegt werden kann, andernfalls **Privat**.<br /><br /> **Wert**<br /> Der Exponent, mit dem die Intensität von Lichtreflexen auf dem aktuellen Pixels definiert wird.|  
|**Normalisierte Zeit**|Die Zeit in Sekunden normalisiert im Bereich \[0, 1\], sodass die Zeit, wenn sie 1 erreicht, auf 0 zurückgesetzt wird.<br /><br /> Sie können diesen Wert als Parameter in Shaderberechnungen verwenden, z. B. um Texturkoordinaten, Farbwerte oder andere Attribute zu animieren.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float`<br /> Die normalisierte Zeit in Sekunden.|Kein|  
|**Uhrzeit**|Die Zeit in Sekunden.<br /><br /> Sie können diesen Wert als Parameter in Shaderberechnungen verwenden, z. B. um Texturkoordinaten, Farbwerte oder andere Attribute zu animieren.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float`<br /> Die Zeit in Sekunden.|Kein|