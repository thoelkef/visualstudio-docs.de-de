---
title: "Filtern von Knoten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7cae2dc-e9a7-49d4-8be5-58b79868624e
caps.latest.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 12
---
# Filtern von Knoten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im Shader\-Designer wird von den Filterknoten eine Eingabe umgewandelt, z. B. ein Farb\- oder Texturmuster in einen bildlichen Farbwert.  Diese bildlichen Farbwerte werden in der Regel beim nicht fotorealistischen Rendering oder als Komponenten für andere visuelle Effekte verwendet.  
  
## Filterknotenverweis  
  
|Knoten|Details|Eigenschaften|  
|------------|-------------|-------------------|  
|**Weichzeichner**|Zeichnet Pixel in einer Textur mithilfe einer Gaußsche Funktion unterstützt.<br /><br /> Sie können dieses verwenden, um Farbdetails oder einem Geräusch versehen in einer Textur zu reduzieren.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten des zu testenden Texels.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Der unscharfe Farbwert.|**Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist, der während des Weichzeichnens verwendet wird.|  
|**Entsättigen**|Reduziert die Farbmenge in der angegebenen Farbe.<br /><br /> Beim Entfernen der Farbe nähert sich der Farbwert seinem Graustufenäquivalent.<br /><br /> **Eingabe:**<br /><br /> `RGB`: `float3`<br /> Die zu entsättigende Farbe.<br /><br /> `Percent`: `float`<br /> Der Prozentsatz der zu entfernenden Farbe, ausgedrückt wie ein normalisierter Wert im Bereich \[0, 1\].<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float3`<br /> Die entsättigte Farbe.|**Sättigung**<br /> Die Gewichtungen, die der Rot\-, Grün\- und Blau\-Farbkomponente zugeordnet sind.|  
|**Kantenerkennung**|Erkennt Kanten in einer Textur mithilfe eines Canny\-Algorithmus.  Kantenpixel werden als weiß ausgegeben, alle anderen als schwarz.<br /><br /> Damit können Sie Kanten in einer Textur identifizieren, sodass auf Kantenpixel zusätzliche Effekte angewendet werden können.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten des zu testenden Texels.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Weiß, wenn das Texel auf einer Kante liegt, andernfalls schwarz.|**Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist, der während der Kantenerkennung verwendet wird.|  
|**Scharfzeichnen**|Schärft eine Textur.<br /><br /> Sie können dieses verwenden, um feine Details in einer Textur hervorzuheben.<br /><br /> **Eingabe:**<br /><br /> `UV`: `float2`<br /> Die Koordinaten des zu testenden Texels.<br /><br /> **Ausgabe:**<br /><br /> `Output`: `float4`<br /> Der unscharfe Farbwert.|**Textur**<br /> Das Texturregister, das dem Sampler zugeordnet ist, der während des Schärfens verwendet wird.|