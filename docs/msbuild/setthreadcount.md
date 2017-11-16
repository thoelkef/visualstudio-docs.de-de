---
title: SetThreadCount | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: SetThreadCount
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 7c25dbb399a3be2af9b181c7ccbf495cc03bec19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="setthreadcount"></a>SetThreadCount
Legt die Anzahl der globalen Threads fest, und weist diese Anzahl für dem aktuellen Thread zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in] `threadCount`  
 Die Anzahl der zu verwendenden Threads.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn die Anzahl der Threads aktualisiert wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** FileTracker.h