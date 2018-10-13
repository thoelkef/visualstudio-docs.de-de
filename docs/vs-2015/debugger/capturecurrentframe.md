---
title: CaptureCurrentFrame | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b33cad0ad67d874ff5595eac7b634cc9810257f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190696"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn derzeit eine andere Erfassung durchgeführt wird – wie etwa eine Erfassung, die durch die `BeginCapture`-Funktion gestartet wurde – dann wird diese Erfassung abgeschlossen und im Grafikprotokoll als gesonderter Frame aufgezeichnet. Direkt im Anschluss beginnt die Grafikdiagnose, den Rest des aktuellen Frames zu erfassen, der ebenfalls als gesonderter Frame aufgezeichnet wird. Das Ende des aktuellen Frames ist durch einen Aufruf von "Present" gekennzeichnet.  
  
 Um einen Frame erfassen zu können, müssen Sie Ihrer app erfassen und Aufzeichnen von Grafikinformationen vorbereiten, d. h. Sie aufgerufen hat, [Init](../debugger/init.md) durch eine Instanz von der `VsgDbg` -Klasse vor dem Aufruf `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Siehe auch  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)



