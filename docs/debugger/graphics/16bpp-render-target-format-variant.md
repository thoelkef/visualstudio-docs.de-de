---
title: 16bpp renderzielformat-renderzielformat-Variante | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a63261a4ef8a6304bec8c2bdde1d9ec9113405e
ms.sourcegitcommit: 8530d15aa72fe058ee3a3b4714c36b8638f8b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188591"
---
# <a name="16-bpp-render-target-format-variant"></a>16 bpp-renderzielformat-Variante
Setzt das Pixelformat für alle Renderziele und Hintergrundpuffer auf DXGI_FORMAT_B5G6R5_UNORM.

## <a name="interpretation"></a>Interpretation
 Ein Renderziel oder ein Hintergrund Puffer verwendet in der Regel ein 32 bpp-Format (32 Bits pro Pixel), z. b. B8G8R8A8_UNORM. 32-bpp-Formate können eine große Menge an Arbeitsspeicher Bandbreite beanspruchen. Da das B5G6R5_UNORM Format ein 16-bpp-Format mit der Hälfte der Größe von 32-bpp-Formaten ist, kann die Verwendung der Arbeitsspeicher Bandbreite, aber auf Kosten der geringeren Farbtreue, den Druck verringern.

 Wenn diese Variante zu einer Leistungssteigerung führt, kann dies ein Zeichen dafür sein, dass Ihre App zu viel Speicherbandbreite verbraucht. Sie können eine deutliche Leistungsverbesserung erzielen, insbesondere dann, wenn der profilierte Frame eine beträchtliche Menge an Überzeichnung oder Alpha Mischung aufweist.

Ein 16-bpp-renderzielformat kann die Speicher Bandgröße mit der Verwendung verringern, wenn Ihre Anwendung die folgenden Bedingungen erfüllt:
- Erfordert keine High-Fidelity-Farb Reproduktion.
- Erfordert keinen Alphakanal.
- Weist nicht oft glatte Farbverläufe auf (die anfällig für das bandgen von Artefakten unter reduzierter Farbtreue sind).

Weitere Strategien zum Reduzieren der Speicherbandbreite sind:
- Reduzieren Sie die Menge der Überzeichnung oder Alpha Mischung.
- Reduzieren Sie die Abmessungen des Frame Puffers.
- Reduzieren Sie die Dimensionen von Textur Ressourcen.
- Reduzieren Sie Komprimierungen von Textur Ressourcen.

Wie gewohnt müssen Sie die Kompromisse bei der Bildqualität bedenken, die mit jeder dieser Optimierungen einhergehen.

Anwendungen, die Teil einer Swapkette sind, haben ein Hintergrund Puffer Format (DXGI_FORMAT_B5G6R5_UNORM), das 16 bpp nicht unterstützt. Diese Austausch Ketten werden mithilfe von `D3D11CreateDeviceAndSwapChain` oder `IDXGIFactory::CreateSwapChain`erstellt. Führen Sie die folgenden Schritte aus, um diese Einschränkung zu umgehen:
1. Erstellen Sie ein Renderziel im B5G6R5_UNORM Format, indem Sie `CreateTexture2D` verwenden und zu diesem Ziel Renderziel.
2. Kopieren Sie das Renderziel auf den Swapkette der Austausch Kette, indem Sie ein voll Bild Quad mit dem Renderziel als Quell Textur zeichnen.
3. Der Austausch ist in der SwapChain vorhanden.

   Wenn diese Strategie mehr Bandbreite spart, als durch Kopieren des Renderziels in den BackBuffer der Austausch Kette beansprucht wird, wird die Renderingleistung verbessert.

   GPU-Architekturen, die gekachelte Rendering-Techniken verwenden, können durch die Verwendung eines 16 bpp-Frame Puffer Formats bedeutende Leistungsvorteile erkennen. Diese Verbesserung liegt daran, dass ein größerer Teil des Frame Puffers in den lokalen Frame Puffer Cache jeder Kachel passen kann. Kachel-Rendering-Architekturen sind manchmal in GPUs in mobilen Handsets und Tablet-Computern zu finden; außerhalb dieser Nische kommen sie selten vor.

## <a name="remarks"></a>Hinweise
 Das Renderzielfomat wird mit jedem Aufruf von `ID3D11Device::CreateTexture2D`, der ein Renderziel erstellt, auf DXGI_FORMAT_B5G6R5_UNORM zurückgesetzt. Vor allem wird das Format überschrieben, wenn das in pDesc übergebene D3D11_TEXTURE2D_DESC-Objekt eines der folgenden Renderziele beschreibt:

- Für das BindFlags-Member ist nur das Flag D3D11_BIND_SHADER_TARGET gesetzt.

- Für das BindFlags-Member ist das Flag D3D11_BIND_DEPTH_STENCIL gelöscht.

- Das Usage-Member ist auf D3D11_USAGE_DEFAULT gesetzt.

## <a name="restrictions-and-limitations"></a>Einschränkungen
 Da das Format B5G6R5 über keinen Alpha-Kanal verfügt, werden Alpha-Inhalte von dieser Variante nicht beibehalten. Wenn das Rendering Ihrer App einen Alpha-Kanal in Ihrem Renderziel erfordert, können Sie nicht einfach zum Format B5G6R5 wechseln.

## <a name="example"></a>Beispiel
 Die **16 bpp-renderzielformat** -Variante kann für Renderziele reproduziert werden, die mit `CreateTexture2D` erstellt wurden, indem Sie Code wie den folgenden verwenden:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
