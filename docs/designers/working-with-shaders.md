---
title: "Arbeiten mit Shaders | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Arbeiten mit Shaders
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können den diagrammbasierten Shader\-Designer in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Entwerfen benutzerdefinierter Shadereffekte verwenden.  Sie können die Shader in Ihrem DirectX\-basierten Spiel oder Ihrer App verwenden.  
  
## Shader  
 Bei einem *Shader* handelt es sich um ein Computerprogramm, mit dem Berechnungen von Grafiken, wie Vertex\-Transformationen oder das Färben von Pixeln ausgeführt werden, und das üblicherweise auf einer Grafikverarbeitungseinheit \(GPU\) anstelle der CPU ausgeführt wird.  Da die meisten Schritte der herkömmlichen fest verdrahteten Grafikpipeline inzwischen von Shaderprogrammen ausgeführt werden, können Sie sie verwenden, um eine den spezifischen Anforderungen Ihrer App angepasste Pipeline zu erstellen.  
  
 Die häufigsten Arten von Shadern sind *Vertex\-Shaders*, mit denen Berechnungen vertexspezifisch ausgeführt werden und die den fest verdrahteten Transformations\- und Beleuchtungsschaltkreis in der nicht programmierbaren Grafikhardware ersetzen, und *Pixel\-Shaders*, mit denen Berechnungen pixelspezifisch ausgeführt werden, die die Farbe eines Pixels bestimmen und den Farbkombinatorschaltkreis mit fester Funktion in der nicht programmierbaren Grafikhardware ersetzen.  Durch die moderne Grafikhardware wurden noch weitere Arten von Shadern möglich: *Hüllen\-Shader*, *Domänen\-Shader* und *Geometrie\-Shader* für Grafikberechnungen und *Compute\-Shader* für Berechnungen außerhalb von Grafiken.  Dieser Phasen sind in der nicht programmierbaren Grafikhardware gar nicht erst verfügbar.  Shader wurden ursprünglich mithilfe einer assemblyähnliche Sprache erstellt, die datenparallele \(SIMD\) und grafikzentrierte\(Skalarprodukt\) Anweisungen gab.  Inzwischen werden Shader in der Regel unter Verwendung höherer C\-ähnlicher Sprachen wie HLSL \(High\-Level Shader Language\) erstellt.  
  
 Sie können den Shader\-Designer verwenden, um Pixel\-Shader interaktiv zu erstellen, anstatt Code einzugeben und zu kompilieren.  Im Shader\-Designer wird ein Shader durch mehrere Knoten definiert, die Daten und Vorgänge darstellen, und durch Verbindungen zwischen Knoten, die das Fließen von Datenwerten und Zwischenergebnissen durch den Shader darstellen.  Durch Verwendung dieses Ansatzes und durch die Echtzeitvorschau im Shader\-Designer können Sie sich die Ausführung des Shaders leichter veranschaulichen und "entdecken" durch Experimentieren interessante Shadervariationen.  
  
## DGSL\-Dokumente  
 Mit dem Shader\-Designer werden Shader im Format der Directed Graph Shader Language \(DGSL\) gespeichert; einem XML\-Format auf Grundlage der Directed Graph Markup Language \(DGML\).  Sie können DGSL\-Shader im Modell\-Editor direkt auf 3D\-Modelle anwenden.  Bevor Sie jedoch einen DGSL\-Shader in der App verwenden können, müssen Sie ihn in ein Format exportieren, das DirectX unterstützt, zum Beispiel das HLSL\-Format.  
  
 Da DGSL mit DGML kompatibel ist, können Sie zur Analyse des DGSL\-Shaders Tools verwenden, die zur Analyse von DGML\-Dokumenten entwickelt wurden.  Informationen zum DGML, finden Sie unter [Grundlegendes graph markup Sprache \(DGML\)](http://msdn.microsoft.com/library/ee842619.aspx).  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Shader\-Designer](../designers/shader-designer.md)|Beschreibt die Verwendung des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shader\-Designers zur Arbeit mit Shadern.|  
|[Shader\-Designer\-Knoten](../designers/shader-designer-nodes.md)|Es werden die Arten von Shader\-Designerknoten erläutert, die Sie verwenden können, um Grafikeffekte zu erzielen.|  
|[Beispiele für den Shader\-Designer](../designers/shader-designer-examples.md)|Stellt Links zu Themen bereit, die die Verwendung des Shader\-Designers veranschaulichen, um allgemeine Grafikeffekte zu erzielen.|