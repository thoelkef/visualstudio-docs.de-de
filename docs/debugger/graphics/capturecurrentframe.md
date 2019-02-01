---
title: CaptureCurrentFrame | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05d93e4cee3fb4969b928caa3ae76112708469f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997233"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Hinweise  
 Wenn derzeit eine andere Erfassung durchgeführt wird – wie etwa eine Erfassung, die durch die `BeginCapture`-Funktion gestartet wurde – dann wird diese Erfassung abgeschlossen und im Grafikprotokoll als gesonderter Frame aufgezeichnet. Direkt im Anschluss beginnt die Grafikdiagnose, den Rest des aktuellen Frames zu erfassen, der ebenfalls als gesonderter Frame aufgezeichnet wird. Das Ende des aktuellen Frames ist durch einen Aufruf von "Present" gekennzeichnet.  
  
 Um einen Frame erfassen zu können, müssen Sie Ihrer app erfassen und Aufzeichnen von Grafikinformationen vorbereiten, d. h. Sie aufgerufen hat, [Init](init.md) durch eine Instanz von der `VsgDbg` -Klasse vor dem Aufruf `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Siehe auch  
 [Init](init.md)   
 [BeginCapture](begincapture.md)