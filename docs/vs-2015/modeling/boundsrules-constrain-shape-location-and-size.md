---
title: Boundsrules schränken die Position und Größe der Form ein | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672726"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules schränken Position und Größe von Formen ein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine Begrenzungs *Regel* ist eine Klasse, die Grenzwerte für die Größe und Position einer Form definiert. Sie stellt eine Methode bereit, die wiederholt aufgerufen wird, während ein Benutzer eine Form oder die Ecken oder Seiten einer Form zieht.

 Im folgenden Beispiel wird eine rechteckige Form als Balken mit fester Größe (horizontal oder vertikal) eingeschränkt. Wenn der Benutzer die Ecken oder Seiten zieht, wird der Umriss zwischen den beiden zulässigen Konfigurationen von Height und Width gedreht.

 Die Begrenzungen-Regel ist eine Klasse, die von <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> abgeleitet ist. Eine Instanz der Regel wird in der Form erstellt:

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

 Beachten Sie, dass der Speicherort und die Größe bei Bedarf eingeschränkt werden können.

## <a name="see-also"></a>Siehe auch
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> [Antworten auf und Weitergeben von Änderungen](../modeling/responding-to-and-propagating-changes.md)
