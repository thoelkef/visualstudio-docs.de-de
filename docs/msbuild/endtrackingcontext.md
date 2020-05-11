---
title: EndTrackingContext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf982200b8e65e404325bdbd189ff3b0f2daebac
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634239"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

Beenden des aktuellen Nachverfolgungskontexts.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>Rückgabewert

Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext beendet wurde.

## <a name="requirements"></a>Anforderungen

**Header:** *FileTracker.h*

## <a name="see-also"></a>Siehe auch

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
