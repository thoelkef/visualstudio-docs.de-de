---
title: Capturecurrentframe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736136"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Erfasst den Rest des aktuellen Frames in der Grafikprotokolldatei.

## <a name="syntax"></a>Syntax

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Hinweise
 Wenn derzeit eine andere Erfassung durchgeführt wird – wie etwa eine Erfassung, die durch die `BeginCapture`-Funktion gestartet wurde – dann wird diese Erfassung abgeschlossen und im Grafikprotokoll als gesonderter Frame aufgezeichnet. Direkt im Anschluss beginnt die Grafikdiagnose, den Rest des aktuellen Frames zu erfassen, der ebenfalls als gesonderter Frame aufgezeichnet wird. Das Ende des aktuellen Frames ist durch einen Aufruf von "Present" gekennzeichnet.

 Um einen Frame zu erfassen, müssen Sie die APP vorbereiten, um Grafik Informationen zu erfassen und aufzuzeichnen – d. h., Sie müssen [Init](init.md) durch eine Instanz der `VsgDbg` Klasse aufgerufen haben, bevor Sie `CaptureCurrentFrame` aufrufen.

## <a name="see-also"></a>Siehe auch
- [Init](init.md)
- [BeginCapture](begincapture.md)