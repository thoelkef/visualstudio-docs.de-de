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
ms.openlocfilehash: 5b1eb28d5a54af1708fa8d3ea7a12887174a15bb
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579588"
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