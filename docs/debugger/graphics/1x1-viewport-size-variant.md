---
title: 1 x 1-Viewportgrößenvariante | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 168b358bf58dcb2c91814f5460b203873255e275
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433245"
---
# <a name="1x1-viewport-size-variant"></a>1x1-Viewportgrößenvariante
Reduziert die Viewport-Dimensionen auf allen Renderzielen auf 1x1 Pixel.  
  
## <a name="interpretation"></a>Interpretation  
 Ein kleinerer Viewport reduziert die Anzahl der Pixel, die Sie zu schattieren. Aber, dass ein kleinerer Viewport nicht reduzieren Sie die Anzahl der Scheitelpunkte, die Sie verarbeiten. Die Einstellung der Viewport-Dimensionen auf 1x1 Pixel eliminiert praktisch die Pixelschattierung aus Ihrer App.  
  
 Wenn diese Variante eine großen Leistungssteigerung führt, kann dies darauf hinweisen, dass Ihre app zu viel Füllrate verbraucht. Darüber hinaus Ihre Lösung ist möglicherweise für die Zielplattform zu hoch oder Ihre app könnte viel Zeit die Schattierung von Pixeln, die später überschrieben werden, auch bekannt als *-Elements zu überzeichnen*. Eine kleinere Framepuffer oder verringern Sie die Menge Alphablendings steigert die Leistung Ihrer app.  
  
## <a name="remarks"></a>Hinweise  
 Die Viewport-Dimensionen werden mit jedem Aufruf von `ID3D11DeviceContext::OMSetRenderTargets` oder `ID3D11DeviceContext::RSSetViewports` auf 1x1 Pixel gesetzt.  
  
## <a name="example"></a>Beispiel  
 Diese Variante kann durch den folgenden Code reproduziert werden:  
  
```cpp
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```
