---
title: BoundsRules schränken Position und Größe von Formen ein
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3028f5b023f40c721d5a81f7b33242463f2425cd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910830"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>BoundsRules schränken Position und Größe von Formen ein

Ein *Begrenzungsregel* ist eine Klasse, die Grenzwerte für die Größe und Position einer Form definiert. Es bietet eine Methode, die wiederholt aufgerufen wird, während ein Benutzer eine Form oder den Ecken oder den Seiten einer Form gezogen wird.

Im folgende Beispiel wird eine rechteckige Form auf eine Leiste mit fester Größe, horizontal oder vertikal sein beschränkt. Wenn der Benutzer den Ecken oder den Seiten zieht, spiegelt die Gliederung, zwischen die beiden zulässigen Konfigurationen der Höhe und Breite.

Die Grenzen Regel ist eine abgeleitete Klasse <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Eine Instanz der Regel wird in der Form erstellt:

```csharp
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

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Reagieren auf und Verteilen von Änderungen](../modeling/responding-to-and-propagating-changes.md)