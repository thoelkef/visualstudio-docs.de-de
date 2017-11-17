---
title: "BoundsRules schränken Position und Größe | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 8a611bd18cb06b712f671d370bfc26d4dc8cf4f3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules schränken Position und Größe von Formen ein
Ein *Grenzen Regel* ist eine Klasse, die Grenzwerte für die Größe und Position einer Form definiert. Es bietet eine Methode, die wiederholt aufgerufen wird, während ein Benutzer eine Form oder den Ecken oder den Seiten einer Form ziehen.  
  
 Das folgende Beispiel schränkt eine rechteckige Form aus, um eine Leiste mit fester Größe, horizontal oder vertikal sein. Wenn der Benutzer den Ecken oder den Seiten zieht, spiegelt die Gliederung zwischen zwei zulässigen Konfigurationen der Höhe und Breite.  
  
 Die Grenzen Regel ist eine abgeleitete Klasse <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Eine Instanz der Regel wird in der Form "erstellt:  
  
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
  
 Beachten Sie, dass sowohl die Position und Größe eingeschränkt werden können, wenn Sie möchten.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md)