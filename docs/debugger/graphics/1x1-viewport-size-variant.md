---
title: 1x1-Anzeigebereichsgrößenvariante | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5b2c96b11c2075ce88b43cdebc34b905141c973
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62848739"
---
# <a name="1x1-viewport-size-variant"></a>1x1-Viewportgrößenvariante
Reduziert die Viewport-Dimensionen auf allen Renderzielen auf 1x1 Pixel.

## <a name="interpretation"></a>Interpretation
 Ein kleinerer Anzeigebereich reduziert die Anzahl der Pixel, die Sie schattieren müssen. Dadurch wird jedoch nicht die Anzahl der Scheitelpunkte verringert, die verarbeitet werden müssen. Die Einstellung der Viewport-Dimensionen auf 1x1 Pixel eliminiert praktisch die Pixelschattierung aus Ihrer App.

 Wenn diese Variante zu einer Leistungssteigerung führt, kann dies ein Zeichen dafür sein, dass Ihre App zu viel Füllrate verbraucht. Außerdem könnte die Auflösung für die Zielplattform zu hoch sein, oder die App benötigt viel Zeit für das Schattieren von Pixeln, die später überschrieben werden (auch *Überzeichnen* genannt). Ein kleinerer Framepuffer oder das Reduzieren der Anzahl von Überzeichnungen erhöhen die Leistungsfähigkeit der App.

## <a name="remarks"></a>Hinweise
 Die Viewport-Dimensionen werden mit jedem Aufruf von `ID3D11DeviceContext::OMSetRenderTargets` oder `ID3D11DeviceContext::RSSetViewports` auf 1x1 Pixel gesetzt.

## <a name="example"></a>Beispiel
 Diese Variante kann mit folgendem Code reproduziert werden:

```cpp
D3D11_VIEWPORT viewport;
viewport.TopLeftX = 0;
viewport.TopLeftY = 0;
viewport.Width = 1;
viewport.Height = 1;
d3d_context->RSSetViewports(1, &viewport);
```
