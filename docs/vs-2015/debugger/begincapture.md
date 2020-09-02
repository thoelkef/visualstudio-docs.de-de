---
title: BeginCapture | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b16fdc4d0a12d7082400e697ca44a7ca4c549f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431796"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Startet ein Erfassungsintervall, das mit `EndCapture` endet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Hinweise  
 Ein Erfassungsintervall umfasst in der Regel eine Teilmenge eines Frames, etwa wenn Sie Grafikinformationen nur über eine bestimmte Art von Zeichnen-Befehl erfassen möchten. Wenn das Erfassungsintervall einen Aufruf von "Present" umfasst, dann werden zwei Frames von Grafikinformationen erfasst. Der erste Frame umfasst das Intervall zwischen dem Aufruf von `BeginCapture` und dem Aufruf von "Present". Das zweite Intervall umfasst das Intervall zwischen dem ersten Direct3D-Ereignis nach dem Aufruf von "Present" und dem Aufruf von `EndCapture`.  
  
 Um ein Intervall zu erfassen, müssen Sie die App so vorbereiten, dass Grafikinformationen erfasst und aufgezeichnet werden, d. h., Sie müssen [Init](../debugger/init.md) über eine Instanz der `VsgDbg`-Klasse aufgerufen haben, bevor Sie `BeginCapture` oder `EndCapture` aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Endcapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)
