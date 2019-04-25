---
title: ResumeTracking | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e2ff32a4eb2218a8b3d09188c787156e484147f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62996698"
---
# <a name="resumetracking"></a>ResumeTracking
Setzt die Nachverfolgung im aktuellen Kontext fort.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>Rückgabewert
 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn die Nachverfolgung fortgesetzt wurde. **E_FAIL** wird zurückgegeben, wenn die Nachverfolgung nicht fortgesetzt werden kann, da der Kontext nicht verfügbar war.

## <a name="requirements"></a>Anforderungen
 **Header:** *FileTracker.h*

## <a name="see-also"></a>Siehe auch
- [SuspendTracking](../msbuild/suspendtracking.md)