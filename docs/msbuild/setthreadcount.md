---
title: SetThreadCount | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9cc9a1ae5f7fb51981f3cebc4d6fa658f614de6d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151839"
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