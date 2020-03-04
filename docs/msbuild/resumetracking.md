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
ms.openlocfilehash: 248bb5e5e01b8209f826478e90b2c60b70922987
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632497"
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