---
title: CaptureCurrentFrame | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fcdeee28077f2c7affd1c4cd1f82d8c8cb29494b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn derzeit eine andere Erfassung durchgeführt wird – wie etwa eine Erfassung, die durch die `BeginCapture`-Funktion gestartet wurde – dann wird diese Erfassung abgeschlossen und im Grafikprotokoll als gesonderter Frame aufgezeichnet. Direkt im Anschluss beginnt die Grafikdiagnose, den Rest des aktuellen Frames zu erfassen, der ebenfalls als gesonderter Frame aufgezeichnet wird. Das Ende des aktuellen Frames ist durch einen Aufruf von "Present" gekennzeichnet.  
  
 Um einen Frame erfassen möchten, müssen Sie Ihre app zu erfassen und Aufzeichnen von Grafikinformationen vorbereiten – d. h. Sie aufgerufen hat, [Init](init.md) über eine Instanz der `VsgDbg` Klasse vor dem Aufruf `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Siehe auch  
 [Init](init.md)   
 [BeginCapture](begincapture.md)