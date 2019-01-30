---
title: StopTrackingAndCleanup | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b6ed74dab67cc2ca718ba312fb657659897c78c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955595"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup
Beendet die Nachverfolgung vollständig und macht Speicherplatz frei, der von der Nachverfolgungssitzung verwendet wird  
  
## <a name="syntax"></a>Syntax  
  
```cpp 
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein **HRESULT** zurück, bei dem **SUCCEEDED** festgelegt ist, wenn die Nachverfolgung beendet wurde  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** *FileTracker.h*  
  
## <a name="see-also"></a>Siehe auch  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)