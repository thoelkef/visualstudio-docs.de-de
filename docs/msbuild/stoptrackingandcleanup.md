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
ms.openlocfilehash: 4a80fcde7aeab601791c033bd21effce175b2cb9
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579563"
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