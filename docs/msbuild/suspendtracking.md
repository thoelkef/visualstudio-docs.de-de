---
title: SuspendTracking| Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 950c6a07a46f7f4b970912e576257a577021367e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632008"
---
# <a name="suspendtracking"></a>SuspendTracking

Hält die Nachverfolgung des aktuellen Kontexts an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>Rückgabewert

 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn die Nachverfolgung angehalten wurde.

## <a name="requirements"></a>Anforderungen

 **Header:** *FileTracker.h*

## <a name="see-also"></a>Siehe auch

- [ResumeTracking](../msbuild/resumetracking.md)