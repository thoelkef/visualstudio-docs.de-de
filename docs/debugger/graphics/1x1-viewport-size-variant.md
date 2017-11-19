---
title: "1 x 1-Viewportgrößenvariante | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 074cf7111108b7ae4f3b6866be19f0a12d3c429b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="1x1-viewport-size-variant"></a>1x1-Viewportgrößenvariante
Reduziert die Viewport-Dimensionen auf allen Renderzielen auf 1x1 Pixel.  
  
## <a name="interpretation"></a>Interpretation  
 Ein kleinerer Viewport reduziert die Anzahl der Pixel, die schattiert werden müssen, jedoch nicht die Anzahl der Scheitelpunkte, die verarbeitet werden müssen. Die Einstellung der Viewport-Dimensionen auf 1x1 Pixel eliminiert praktisch die Pixelschattierung aus Ihrer App.  
  
 Wenn diese Variante zu einer Leistungssteigerung führt, kann dies ein Zeichen dafür sein, dass Ihre App zu viel Füllrate verbraucht. Dies kann ein Zeichen dafür sein, dass die gewählte Auflösung für die Zielplattform zu hoch ist oder dass Ihre App sehr viel Zeit für die Schattierung von Pixeln verwendet, die später überschrieben (überzeichnet) werden. Dieses Ergebnis legt nahe, dass eine Senkung der Größe Ihres Framepuffers oder der Menge von Überzeichnungen die Leistung Ihrer App erhöht.  
  
## <a name="remarks"></a>Hinweise  
 Die Viewport-Dimensionen werden mit jedem Aufruf von `ID3D11DeviceContext::OMSetRenderTargets` oder `ID3D11DeviceContext::RSSetViewports` auf 1x1 Pixel gesetzt.  
  
## <a name="example"></a>Beispiel  
 Diese Variante kann durch einen Code reproduziert werden, der dem folgenden ähnlich ist:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```