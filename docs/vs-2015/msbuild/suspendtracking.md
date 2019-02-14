---
title: SuspendTracking| Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- SuspendTracking
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a72045e7e03a21bd827be1501251db823ca6ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782544"
---
# <a name="suspendtracking"></a>SuspendTracking
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Hält die Nachverfolgung des aktuellen Kontexts an.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT WINAPI SuspendTracking(void);  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein <!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->HRESULT<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->, bei dem SUCCEEDED festgelegt ist, wenn die Nachverfolgung angehalten wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** FileTracker.h  
  
## <a name="see-also"></a>Siehe auch  
 [ResumeTracking](../msbuild/resumetracking.md)
