---
title: Halbquarter Textur Dimensionen Variant | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 620300d1727adc41d5655bd33dde87ad592bba1c
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252988"
---
# <a name="halfquarter-texture-dimensions-variant"></a>Halb-/Viertel-Texturdimensionsvariante
Reduziert die Texturdimensionen auf Texturen, die keine Renderziele sind.

## <a name="interpretation"></a>Interpretation
 Kleinere Texturen belegen weniger Speicherplatz und verbrauchen deshalb weniger Bandbreite und entlasten den Druck auf den Texturcache der GPU. Allerdings kann ihre geringere Detailliertheit zu niedriger Bildqualität führen, besonders, wenn sie in einer 3D-Szene aus der Nähe oder vergrößert betrachtet werden.

 Wenn diese Variante zu einer großen Leistungssteigerung führt, kann dies bedeuten, dass Ihre App zu viel Speicherbandbreite verbraucht oder den Texturcache ineffizient verwendet oder beides. Es kann auch bedeuten, dass Ihre Texturen mehr GPU-Speicherplatz belegen, als verfügbar ist, wodurch die Texturen in den Systemspeicher ausgelagert werden.

 Wenn Ihre App zu viel Speicherbandbreite verbraucht oder den Texturcache ineffizient verwendet, können Sie die Größe Ihrer Texturen ändern, sollten jedoch vorher die Aktivierung von Mipmaps für geeignete Texturen in Erwägung ziehen. Wie kleinere Texturen verbrauchen auch Mipmap-Texturen weniger Speicherbandbreite – obwohl sie mehr GPU-Speicher belegen – und erhöhen die Cache-Nutzung, aber sie reduzieren keine Texturdetails. Wir empfehlen Mipmaps immer dann, wenn Texturen trotz erhöhter Speichernutzung nicht in den Systemspeicher ausgelagert werden.

 Wenn Ihre Texturen mehr GPU-Speicher belegen, als verfügbar ist, können Sie die Größe der Texturen ändern, sollten aber vorher überlegen, dafür geeignete Texturen zu komprimieren. Wie kleinere Texturen verbrauchen auch komprimierte Texturen weniger Speicher, so dass eine Auslagerung in den Systemspeicher nicht notwendig ist, aber die Farbtreue sinkt ebenfalls. Die Komprimierung ist nicht für alle Texturen geeignet – z. B. nicht für Texturen mit deutlichen Farbvariationen in einem kleinen Bereich. Aber für viele Texturen lässt sich mit der Komprimierung eine allgemeine Bildqualität besser aufrechterhalten als durch Reduzierung ihrer Größe.

## <a name="remarks"></a>Hinweise
 Texturdimensionen werden mit jedem Aufruf von `ID3D11Device::CreateTexture2D`, der eine Quelltextur erzeugt, reduziert. Texturdimensionen werden vor allem reduziert, wenn das in `pDesc` übergebene D3D11_TEXTURE2D_DESC-Objekt eine in einem Rendering beschriebene Textur beschreibt, z. B.:

- Für das BindFlags-Member ist nur das Flag D3D11_BIND_SHADER_RESOURCE gesetzt.

- Für das MiscFlags-Member ist das Flag D3D11_RESOURCE_MISC_TILE_POOL oder D3D11_RESOURCE_MISC_TILED nicht festgelegt (die Größe unterteilter Ressourcen wird nicht geändert).

- Das Texturformat wird nicht als Renderziel unterstützt – wie von D3D11_FORMAT_SUPPORT_RENDER_TARGET festgelegt –, was aber für die Reduzierung der Texturgröße erforderlich ist. Die Formate BC1, BC2 und BC3 werden ebenfalls unterstützt, auch wenn sie nicht als Renderziele unterstützt werden.

  Wenn Ursprungsdaten von der Anwendung bereitgestellt werden, skaliert diese Variante diese Texturdaten auf die passende Größe, bevor sie die Textur erstellt. Wenn die Ursprungsdaten in einem blockkomprimierten Format wie BC1, BC2 oder BC3 ausgegeben werden, werden sie dekodiert, skaliert und wieder kodiert, um eine kleinere Textur zu erstellen. (Blockkomprimierung bedeutet, dass das Verfahren der Dekodierung, Skalierung und Neukodierung zu einer geringeren Bildqualität führt, als wenn eine blockkomprimierte Textur aus einer skalierten Version der Textur erstellt wird, die vorher nicht kodiert wurde.)

  Wenn Mipmaps für die Textur aktiviert werden, reduziert die Variante die Anzahl der Mip-Ebenen entsprechend – um eine Ebene, wenn auf halbe Größe skaliert wird, oder um zwei Ebenen, wenn auf Viertelgröße skaliert wird.

## <a name="example"></a>Beispiel
 Diese Variante ändert die Größe von Texturen zur Laufzeit vor dem Aufruf `CreateTexture2D`von. Wir empfehlen bei diesem Ansatz die Verwendung eines Produktionscodes, da die Texturen in vollständiger Größe mehr Speicherplatz verbrauchen und der zusätzliche Schritt die Ladezeiten in Ihrer App bedeutend in die Länge ziehen kann – insbesondere bei komprimierten Texturen, für denen Kodierung beträchtliche Computerressourcen erforderlich sind. Wir empfehlen, die Größe Ihrer Texturen stattdessen mithilfe eines Bildeditors oder Bildprozessors, der Teil Ihrer Erstellungspipeline ist, offline zu ändern. Diese Ansätze reduzieren Speicheranforderungen, eliminieren den Laufzeit-Overhead in Ihrer App und wenden mehr Bearbeitungszeit auf, sodass Sie die beste Bildqualität erreichen, wenn Sie Ihre Texturen verkleinern oder komprimieren.

## <a name="see-also"></a>Siehe auch
- [Mipmap-Generierungsvariante](mip-map-generation-variant.md)
- [BC-Texturkomprimierungsvariante](bc-texture-compression-variant.md)