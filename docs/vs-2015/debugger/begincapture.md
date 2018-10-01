---
title: BeginCapture | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f9bc573799ddb5fdd094c7c0e571a88c13b5420
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510414"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [BeginCapture](https://docs.microsoft.com/visualstudio/debugger/graphics/begincapture).  
  
Startet ein Erfassungsintervall, das mit `EndCapture` endet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>Hinweise  
 Ein Erfassungsintervall umfasst in der Regel eine Teilmenge eines Frames, etwa wenn Sie Grafikinformationen nur über eine bestimmte Art von Zeichnen-Befehl erfassen möchten. Wenn das Erfassungsintervall einen Aufruf von "Present" umfasst, dann werden zwei Frames von Grafikinformationen erfasst. Der erste Frame umfasst das Intervall zwischen dem Aufruf von `BeginCapture` und dem Aufruf von "Present". Das zweite Intervall umfasst das Intervall zwischen dem ersten Direct3D-Ereignis nach dem Aufruf von "Present" und dem Aufruf von `EndCapture`.  
  
 Um ein Intervall zu erfassen, müssen Sie Ihrer app erfassen und Aufzeichnen von Grafikinformationen vorbereiten, d. h. Sie aufgerufen hat, [Init](../debugger/init.md) durch eine Instanz der dem `VsgDbg` -Klasse vor dem Aufruf `BeginCapture` oder `EndCapture`.  
  
## <a name="see-also"></a>Siehe auch  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)



