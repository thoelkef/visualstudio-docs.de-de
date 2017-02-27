---
title: "Shader-Designer-Knoten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 6
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 6
---
# Shader-Designer-Knoten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Artikel in diesem Abschnitt der Dokumentation enthalten Informationen zu den verschiedenen Knoten von Shader\-Designer, mit denen Sie Grafikeffekte erstellen können.  
  
## Knoten und Knotentypen  
 Der Shader\-Designer stellt visuelle Effekte als Diagramm dar.  Diese Diagramme werden von den Knoten erstellt, die speziell ausgewählt und auf präzise Weise miteinander verbunden werden, um den beabsichtigten Effekt zu erzielen.  Jeder Knoten stellt entweder eine Information oder eine mathematische Funktion dar. Die Verbindungen zwischen den Knoten geben an, wie die Informationen durch das Diagramm fließen, um das Ergebnis zu erzeugen.  Der Shader\-Designer stellt sechs verschiedene Knotentypen bereit – Filter, Texturknoten, Parameter, Konstanten, Hilfsprogramm\-Knoten und Mathematikknoten. Zu jedem Typ gehören mehrere einzelne Knoten.  Diese Knoten und Knotentypen werden in den anderen Artikeln in diesem Abschnitt beschrieben – siehe die Links am Ende dieses Dokuments.  
  
## Knotenstruktur  
 Alle Knoten bestehen aus einer Kombination gemeinsamer Elemente.  Jeder Knoten verfügt über mindestens ein Ausgabeterminal auf der rechten Seite \(außer dem abschließenden Farbknoten, der die Ausgabe des Shaders darstellt\).  Knoten, die Berechnungen oder Texturbeispiele darstellen, verfügen links über Eingabeterminals. Knoten, die Informationen darstellen, verfügen über keine Eingabeterminals.  Ausgabeterminals werden mit Eingabeterminals verbunden, um Informationen von einem Knoten zum anderen zu übergeben.  
  
### Erweiterung von Eingaben  
 Da der Shader\-Designer HLSL\-Quellcode generieren muss, damit der Effekt in einem Spiel oder in einer App verwendet werden kann, unterliegen die Knoten des Shader\-Designers den Regeln der Typerweiterung, die HLSL verwendet.  Da Grafikhardware hauptsächlich auf Gleitkommawerten operiert, ist eine Typerweiterung zwischen verschiedenen Typen, z. B. aus `int` in `float` oder aus `float` in `double` eher selten.  Da die Grafikhardware denselben Vorgang für mehrere Informationen sofort anwendet, kann stattdessen eine andere Art von Erweiterung stattfinden, bei der die kürzere einer Reihe von Eingaben verlängert wird, um der Größe der längsten Eingabe zu entsprechen.  Wie sie verlängert wird, hängt vom Typ der Eingabe und auch vom Vorgang selbst ab:  
  
-   **Wenn der kleinere Typ ein Skalarwert ist, dann gilt Folgendes:**  
  
     Der Wert des Skalars wird in einen Vektor repliziert, der gleich groß wie die größere Eingabe ist.  Beispielsweise wird die skalare Eingabe 5,0 zum Vektor \(5,0, 5,0, 5,0\), wenn die größte Eingabe des Vorgangs ein Vektor aus drei Elementen ist, und zwar unabhängig von der Art des Vorgangs.  
  
-   **Wenn der kleinere Typ ein Vektor ist und der Vorgang multiplikativ \(\*,\/, % usw.\) ist, dann gilt Folgendes:**  
  
     Der Wert des Vektors wird in die führenden Elemente eines Vektors kopiert, der gleich groß wie größere Eingabe ist, und die nachfolgenden Elemente werden auf 1,0 festgelegt.  Beispielsweise wird die Vektoreingabe \(5,0, 5,0\) zum Vektor \(5,0, 5,0, 1,0, 1,0\), wenn sie mit einem Vektor aus vier Elementen multipliziert wird.  Dadurch werden das dritte und vierte Elemente der Ausgabe beibehalten, da die multiplikative Identität, also 1,0, verwendet wird.  
  
-   **Wenn der kleinere Typ ein Vektor ist, und der Vorgang additiver Natur \(\+, \- usw.\) ist, dann gilt Folgendes:**  
  
     Der Wert des Vektors wird in die führenden Elemente eines Vektors kopiert, der gleich groß wie größere Eingabe ist, und die nachfolgenden Elemente werden auf 0,0 festgelegt.  Beispielsweise wird die Vektoreingabe \(5,0, 5,0\) zum Vektor \(5,0, 5,0, 0,0, 0,0\), wenn sie zu einem Vektor mit vier Elementen addiert wird.  Dadurch werden das dritte und vierte Elemente der Ausgabe beibehalten, da die additive Identität, also 0,0, verwendet wird.  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[Konstante Knoten](../designers/constant-nodes.md)|Beschreibt Knoten, die Sie verwenden können, um Literalwerte und interpolierte Vertex\-Zustandsinformationen in den Shader\-Berechnungen darzustellen.  Da der Vertex\-Zustand interpoliert wird – und deshalb für jedes Pixel unterschiedlich ist –, erhält jede Pixel\-Shader\-Instanz eine andere Version der Konstante.|  
|[Parameterknoten](../designers/parameter-nodes.md)|Beschreibt Knoten, die Sie verwenden können, um Kameraposition, Materialeigenschaften, Beleuchtungsparameter, Zeit und andere Informationen zum App\-Zustand in Shader\-Berechnungen darzustellen.|  
|[Texturknoten](../designers/texture-nodes.md)|Beschreibt die Knoten, die Sie verwenden können, um verschiedene Texturtypen und Geometrien zu berechnen und Texturkoordinaten auf herkömmliche Weise zu erstellen oder umzuwandeln.|  
|[Berechnungsknoten](../designers/math-nodes.md)|Beschreibt die Knoten, die Sie verwenden können, um algebraische, logische, trigonometrische und andere mathematische Operationen durchzuführen, die präzise auf die HLSL\-Anweisungen abgestimmt sind.|  
|[Hilfsprogrammknoten](../designers/utility-nodes.md)|Beschreibt die Knoten, die Sie verwenden können, um allgemeine Beleuchtungsberechnungen und andere allgemeine Vorgänge auszuführen, die nicht präzise auf die HLSL\-Anweisungen abgestimmt sind.|  
|[Filtern von Knoten](../designers/filter-nodes.md)|Beschreibt die Knoten, die Sie verwenden können, um eine Textur\- und Farbfilterung durchzuführen.|