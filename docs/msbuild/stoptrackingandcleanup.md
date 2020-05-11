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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee30bf031761fa7920dadad04d8f17a1bcc0b3a2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631990"
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

- [StartTrackingContext](../msbuild/starttrackingcontext.md)