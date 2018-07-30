---
title: SuspendTracking| Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0d52fb5d50a75207a0aad49f7b29cfc66b8e889
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154195"
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
 [ResumeTracking](../msbuild/resumetracking.md)