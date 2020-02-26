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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bb4663013a73d88ed7c2118816007705834162c
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578453"
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