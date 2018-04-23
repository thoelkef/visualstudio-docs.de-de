---
title: EndCapture | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27fc4053fdfbfe767e72b9b5511ab3660cd7b4b8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
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
 [beginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)