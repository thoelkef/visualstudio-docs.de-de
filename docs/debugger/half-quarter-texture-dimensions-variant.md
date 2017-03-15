---
title: "Halb-/Viertel-Texturdimensionsvariante | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Halb-/Viertel-Texturdimensionsvariante
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Reduziert die Texturdimensionen auf Texturen, die keine Renderziele sind.  
  
## Interpretation  
 Kleinere Texturen belegen weniger Speicherplatz und verbrauchen deshalb weniger Bandbreite und entlasten den Druck auf den Texturcache der GPU.  Allerdings kann ihre geringere Detailliertheit zu niedriger Bildqualität führen, besonders, wenn sie in einer 3D\-Szene aus der Nähe oder vergrößert betrachtet werden.  
  
 Wenn diese Variante zu einer großen Leistungssteigerung führt, kann dies bedeuten, dass Ihre App zu viel Speicherbandbreite verbraucht oder den Texturcache ineffizient verwendet oder beides.  Es kann auch bedeuten, dass Ihre Texturen mehr GPU\-Speicherplatz belegen, als verfügbar ist, wodurch die Texturen in den Systemspeicher ausgelagert werden.  
  
 Wenn Ihre App zu viel Speicherbandbreite verbraucht oder den Texturcache ineffizient verwendet, können Sie die Größe Ihrer Texturen ändern, sollten jedoch vorher die Aktivierung von Mipmaps für geeignete Texturen in Erwägung ziehen.  Wie kleinere Texturen verbrauchen auch Mipmap\-Texturen weniger Speicherbandbreite – obwohl sie mehr GPU\-Speicher belegen – und erhöhen die Cache\-Nutzung, aber sie reduzieren keine Texturdetails.  Wir empfehlen Mipmaps immer dann, wenn Texturen trotz erhöhter Speichernutzung nicht in den Systemspeicher ausgelagert werden.  
  
 Wenn Ihre Texturen mehr GPU\-Speicher belegen, als verfügbar ist, können Sie die Größe der Texturen ändern, sollten aber vorher überlegen, dafür geeignete Texturen zu komprimieren.  Wie kleinere Texturen verbrauchen auch komprimierte Texturen weniger Speicher, so dass eine Auslagerung in den Systemspeicher nicht notwendig ist, aber die Farbtreue sinkt ebenfalls.  Die Komprimierung ist nicht für alle Texturen geeignet – z. B. nicht für Texturen mit deutlichen Farbvariationen in einem kleinen Bereich. Aber für viele Texturen lässt sich mit der Komprimierung eine allgemeine Bildqualität besser aufrechterhalten als durch Reduzierung ihrer Größe.  
  
## Hinweise  
 Texturdimensionen werden mit jedem Aufruf von `ID3D11Device::CreateTexture2D`, der eine Quelltextur erzeugt, reduziert.  Texturdimensionen werden vor allem reduziert, wenn das in `pDesc` übergebene D3D11\_TEXTURE2D\_DESC\-Objekt eine in einem Rendering beschriebene Textur beschreibt, z. B.:  
  
-   Für das BindFlags\-Member ist nur das Flag D3D11\_BIND\_SHADER\_RESOURCE gesetzt.  
  
-   Für das MiscFlags\-Member ist das Flag D3D11\_RESOURCE\_MISC\_TILE\_POOL oder D3D11\_RESOURCE\_MISC\_TILED nicht festgelegt \(die Größe unterteilter Ressourcen wird nicht geändert\).  
  
-   Das Texturformat wird nicht als Renderziel unterstützt – wie von D3D11\_FORMAT\_SUPPORT\_RENDER\_TARGET festgelegt –, was aber für die Reduzierung der Texturgröße erforderlich ist.  Die Formate BC1, BC2 und BC3 werden ebenfalls unterstützt, auch wenn sie nicht als Renderziele unterstützt werden.  
  
 Wenn Ursprungsdaten von der Anwendung bereitgestellt werden, skaliert diese Variante diese Texturdaten auf die passende Größe, bevor sie die Textur erstellt.  Wenn die Ursprungsdaten in einem blockkomprimierten Format wie BC1, BC2 oder BC3 ausgegeben werden, werden sie dekodiert, skaliert und wieder kodiert, um eine kleinere Textur zu erstellen.  \(Blockkomprimierung bedeutet, dass das Verfahren der Dekodierung, Skalierung und Neukodierung zu einer geringeren Bildqualität führt, als wenn eine blockkomprimierte Textur aus einer skalierten Version der Textur erstellt wird, die vorher nicht kodiert wurde.\)  
  
 Wenn Mipmaps für die Textur aktiviert werden, reduziert die Variante die Anzahl der Mip\-Ebenen entsprechend – um eine Ebene, wenn auf halbe Größe skaliert wird, oder um zwei Ebenen, wenn auf Viertelgröße skaliert wird.  
  
## Beispiel  
 Diese Variante ändert die Größe von Texturen vor dem Aufruf von `CreateTexture2D`.  Wir empfehlen bei diesem Ansatz die Verwendung eines Produktionscodes, da die Texturen in vollständiger Größe mehr Speicherplatz verbrauchen und der zusätzliche Schritt die Ladezeiten in Ihrer App bedeutend in die Länge ziehen kann – insbesondere bei komprimierten Texturen, für denen Kodierung beträchtliche Computerressourcen erforderlich sind.  Wir empfehlen, die Größe Ihrer Texturen stattdessen mithilfe eines Bildeditors oder Bildprozessors, der Teil Ihrer Erstellungspipeline ist, offline zu ändern.  Diese Ansätze reduzieren den Speicherbedarf, eliminieren den Laufzeit\-Overhead in Ihrer App und wenden mehre Bearbeitungszeit auf, sodass Sie die beste Bildqualität erreichen, wenn Sie Ihre Texturen verkleinern oder komprimieren.  
  
## Siehe auch  
 [Mipmap\-Generierungsvariante](../debugger/mip-map-generation-variant.md)   
 [BC\-Texturkomprimierungsvariante](../debugger/bc-texture-compression-variant.md)