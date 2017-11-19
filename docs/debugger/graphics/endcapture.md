---
title: EndCapture | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f587b10fea4b593234be2a536baa13cf7b3db66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="endcapture"></a>EndCapture
Beendet ein Erfassungsintervall, das mit `BeginCapture` gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Hinweise  
 Ein Erfassungsintervall umfasst in der Regel eine Teilmenge eines Frames, etwa wenn Sie Grafikinformationen nur über eine bestimmte Art von Zeichnen-Befehl erfassen möchten. Wenn das Erfassungsintervall einen Aufruf von "Present" umfasst, dann werden zwei Frames von Grafikinformationen erfasst. Der erste Frame umfasst das Intervall zwischen dem Aufruf von `BeginCapture` und dem Aufruf von "Present". Das zweite Intervall umfasst das Intervall zwischen dem ersten Direct3D-Ereignis nach dem Aufruf von "Present" und dem Aufruf von `EndCapture`.  
  
 Um ein Intervall zu erfassen, müssen Sie Ihre app zu erfassen und Aufzeichnen von Grafikinformationen vorbereiten – d. h. Sie aufgerufen hat, [Init](init.md) über eine Instanz der `VsgDbg` Klasse vor dem Aufruf `BeginCapture` oder `EndCapture`.  
  
## <a name="see-also"></a>Siehe auch  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)