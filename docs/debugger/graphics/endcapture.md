---
title: EndCapture | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 320898ad028015085448b706e4962ae4050d8b2f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950620"
---
# <a name="endcapture"></a>EndCapture
Beendet ein Erfassungsintervall, das mit `BeginCapture` gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Hinweise  
 Ein Erfassungsintervall umfasst in der Regel eine Teilmenge eines Frames, etwa wenn Sie Grafikinformationen nur über eine bestimmte Art von Zeichnen-Befehl erfassen möchten. Wenn das Erfassungsintervall einen Aufruf von "Present" umfasst, dann werden zwei Frames von Grafikinformationen erfasst. Der erste Frame umfasst das Intervall zwischen dem Aufruf von `BeginCapture` und dem Aufruf von "Present". Das zweite Intervall umfasst das Intervall zwischen dem ersten Direct3D-Ereignis nach dem Aufruf von "Present" und dem Aufruf von `EndCapture`.  
  
 Um ein Intervall zu erfassen, müssen Sie Ihrer app erfassen und Aufzeichnen von Grafikinformationen vorbereiten, d. h. Sie aufgerufen hat, [Init](init.md) durch eine Instanz der dem `VsgDbg` -Klasse vor dem Aufruf `BeginCapture` oder `EndCapture`.  
  
## <a name="see-also"></a>Siehe auch  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)