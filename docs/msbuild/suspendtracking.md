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
ms.openlocfilehash: d48c29b9dcca477c5a5470c443be08d5060b413d
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578113"
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