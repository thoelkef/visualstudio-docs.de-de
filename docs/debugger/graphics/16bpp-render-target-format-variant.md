---
title: 16bpp-Renderzielformat-Variante zu rendern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e9a8e990ee3b95d93f8757f54b92c808fb650f8
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433327"
---
# <a name="16-bpp-render-target-format-variant"></a>16 Bit pro Pixel-Renderzielformat-Variante
Setzt das Pixelformat für alle Renderziele und Hintergrundpuffer auf DXGI_FORMAT_B5G6R5_UNORM.  
  
## <a name="interpretation"></a>Interpretation  
 Ein Renderziel oder ein Hintergrundpuffer verwendet in der Regel ein 32 Bpp (32 Bits pro Pixel)-Format z. B. B8G8R8A8_UNORM. 32-Bpp-Formate können eine große Menge an Bandbreite nutzen. Da das Format B5G6R5_UNORM ein 16-Bit-pro-Pixel-Format, die halb so groß wie die 32-Bpp-Formate ist handelt, können sie mit Auslastung des Speicherbandbreite, jedoch auch zu reduzierter Farbtreue reduzieren.  
  
 Wenn diese Variante zu einer Leistungssteigerung führt, kann dies ein Zeichen dafür sein, dass Ihre App zu viel Speicherbandbreite verbraucht. Insbesondere dann, wenn der profilierte Rahmen eine beträchtliche Menge an überzeichnen oder Alphablending hatten, erhalten Sie deutliche leistungsverbesserung.

Eine 16-Bit-pro-Pixel-renderzielformat kann Arbeitsspeicher-Band-Nutzung verringern, wenn Ihre Anwendung die folgenden Bedingungen:
- Ist kein hoher Farbtreue erforderlich.
- Sie erfordert keine alpha-Kanal.
- Keine Ofent weichen Gradienten (die Bereichsmethoden Artefakten unter reduzierter Farbtreue anfällig sind).

Sind andere Strategien, um Bandbreite zu reduzieren:
- Verringern der Anzahl der überzeichnen oder Alphablending.
- Reduzieren Sie die Dimensionen der der Framepuffer.
- Reduzieren Sie die Abmessungen des texturressourcen.
- Reduzieren Sie protokollkomprimierungen des texturressourcen.
 
Wie gewohnt müssen Sie die Kompromisse bei der Bildqualität bedenken, die mit jeder dieser Optimierungen einhergehen.  

Anwendungen, die Teil einer Swapkette erläutert haben ein Hintergrundpuffer-Format (DXGI_FORMAT_B5G6R5_UNORM) an, die 16 Bit pro Pixel nicht unterstützt. Dieser Swapketten Erstellung erfolgt mithilfe von `D3D11CreateDeviceAndSwapChain` oder `IDXGIFactory::CreateSwapChain`. Um diese Einschränkung zu umgehen, führen Sie die folgenden Schritte aus:
1. Erstellen Sie ein Renderziel im Format B5G6R5_UNORM mithilfe `CreateTexture2D` und für die Zielplattform rendern. 
2. Kopieren Sie das Renderziel auf die der Swapkette, indem Sie eine Vollbild-Quad mit dem Renderziel als Quelltextur zeichnen.
3. Rufen Sie auf Ihrer Swapkette vorhanden.

 Wenn diese Strategie mehr Bandbreite als genutzt werden, indem Sie das Renderziel in der Swapkette kopieren gespeichert wird, wird dann Renderingleistung verbessert.

 GPU-Architekturen, die Kachel-Rendering-Techniken verwenden sehen beachtliche Leistungsvorteile mithilfe eines 16 Bit pro Pixel-Frame-Puffer-Formats. Diese Verbesserung ist, da ein größerer Teil der Framepuffer im Puffercache für jede Kachel in der lokalen Frame eingepasst werden kann. Kachel-Rendering-Architekturen sind manchmal in GPUs in mobilen Handsets und Tablet-Computern zu finden; außerhalb dieser Nische kommen sie selten vor.  
  
## <a name="remarks"></a>Hinweise  
 Das Renderzielfomat wird mit jedem Aufruf von `ID3D11Device::CreateTexture2D`, der ein Renderziel erstellt, auf DXGI_FORMAT_B5G6R5_UNORM zurückgesetzt. Vor allem wird das Format überschrieben, wenn das in pDesc übergebene D3D11_TEXTURE2D_DESC-Objekt eines der folgenden Renderziele beschreibt:  
  
-   Für das BindFlags-Member ist nur das Flag D3D11_BIND_SHADER_TARGET gesetzt.  
  
-   Für das BindFlags-Member ist das Flag D3D11_BIND_DEPTH_STENCIL gelöscht.  
  
-   Das Usage-Member ist auf D3D11_USAGE_DEFAULT gesetzt.  
  
## <a name="restrictions-and-limitations"></a>Einschränkungen  
 Da das Format B5G6R5 über keinen Alpha-Kanal verfügt, werden Alpha-Inhalte von dieser Variante nicht beibehalten. Wenn das Rendering Ihrer App einen Alpha-Kanal in Ihrem Renderziel erfordert, können Sie nicht einfach zum Format B5G6R5 wechseln.  
  
## <a name="example"></a>Beispiel  
 Die **16 Bit pro Pixel Renderzielformat** Variante für mithilfe von erstellte Renderziele reproduziert werden kann `CreateTexture2D` mithilfe von Code wie folgt:  
  
```cpp
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
