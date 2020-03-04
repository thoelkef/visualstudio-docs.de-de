---
title: SetThreadCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 102f46ec639719bb2bec70a38c6c7177c63793c1
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632328"
---
# <a name="setthreadcount"></a>SetThreadCount

Legt die Anzahl der globalen Threads fest, und weist diese Anzahl für dem aktuellen Thread zu.

## <a name="syntax"></a>Syntax

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>Parameter

[in] `threadCount`

 Die Anzahl der zu verwendenden Threads.

## <a name="return-value"></a>Rückgabewert

 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn die Anzahl der Threads aktualisiert wurde.

## <a name="requirements"></a>Anforderungen

 **Header:** *FileTracker.h*