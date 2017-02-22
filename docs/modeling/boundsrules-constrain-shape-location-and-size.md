---
title: "BoundsRules schr&#228;nken Position und Gr&#246;&#223;e von Formen ein | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Ereignisse"
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 18
caps.handback.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# BoundsRules schr&#228;nken Position und Gr&#246;&#223;e von Formen ein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine *Grenzen\-Regel* ist eine Klasse, die Begrenzungen für die Größe und Position einer Form definiert.  Sie enthält eine Methode, die wiederholt aufgerufen wird, wenn ein Benutzer eine Form oder die Ecken oder die Seiten einem Formular ziehen.  
  
 Im folgenden Beispiel wird eine rechteckige Form ein, um eine Leiste feste Größe ist entweder horizontal oder vertikal.  Wenn der Benutzer die Ecken oder Seiten, die Gliederung leichten schläge zwischen den beiden zulässigen Konfigurationen von Höhe und Breite gezogen wird.  
  
 Die Grenzen die Regel ist eine Klasse, die von <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>abgeleitet ist.  Eine Instanz der Regel wird im Format erstellt:  
  
```  
using Microsoft.VisualStudio.Modeling.Diagrams; ...  
public partial class BarShape  
{  
  /// <summary>  
  /// Rule invoked when the user is resizing a shape.  
  /// </summary>  
  public override BoundsRules BoundsRules  
  { get { return new BarBoundsRule(); } }  
}  
/// <summary>  
/// Rule invoked when the user is changing a shape's outline.  
/// Provides real-time mouse rubber-band feedback, so must work fast.  
/// </summary>  
public class BarBoundsRule: BoundsRules  
{   
  public override RectangleD GetCompliantBounds   
     (ShapeElement shape, RectangleD proposedBounds)  
  {  
    double thickness = 0.1;  
    if (proposedBounds.Height > proposedBounds.Width)  
    {  
      // There is a minimum width for a shape; the width  
      // will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
            new SizeD(thickness, proposedBounds.Height));  
    }  
    else  
    {  
      // There is a minimum height for a shape; the   
      // height will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
         new SizeD(proposedBounds.Width, thickness));  
} } }  
```  
  
 Beachten Sie, dass der Position und Größe beschränkt werden können.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)