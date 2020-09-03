---
title: CaptureCurrentFrame | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161634"
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
  
 Um Frames zu erfassen, müssen Sie die App so vorbereiten, dass Grafikinformationen erfasst und aufgezeichnet werden, d. h., Sie müssen [Init](../debugger/init.md) über eine Instanz der `VsgDbg`-Klasse aufgerufen haben, bevor Sie `CaptureCurrentFrame` aufrufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
