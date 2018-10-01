---
title: BoundsRules schränken Position und Größe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: cafcf44bc1365b74474b201a01d0089465cc7430
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515830"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules schränken Position und Größe von Formen ein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [BoundsRules einschränken Position und Größe](https://docs.microsoft.com/visualstudio/modeling/boundsrules-constrain-shape-location-and-size).  
  
Ein *Begrenzungsregel* ist eine Klasse, die Grenzwerte für die Größe und Position einer Form definiert. Es bietet eine Methode, die wiederholt aufgerufen wird, während ein Benutzer eine Form oder den Ecken oder den Seiten einer Form gezogen wird.  
  
 Im folgende Beispiel wird eine rechteckige Form auf eine Leiste mit fester Größe, horizontal oder vertikal sein beschränkt. Wenn der Benutzer den Ecken oder den Seiten zieht, spiegelt die Gliederung, zwischen die beiden zulässigen Konfigurationen der Höhe und Breite.  
  
 Die Grenzen Regel ist eine abgeleitete Klasse <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Eine Instanz der Regel wird in der Form erstellt:  
  
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



