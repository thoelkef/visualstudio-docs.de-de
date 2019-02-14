---
title: ResumeTracking | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- ResumeTracking
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2328b318c00b214138cf70e505c1988f8f1afc6a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802201"
---
# <a name="resumetracking"></a>ResumeTracking
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Setzt die Nachverfolgung im aktuellen Kontext fort.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein <!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->HRESULT<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->, bei dem SUCCEEDED festgelegt ist, wenn die Nachverfolgung fortgesetzt wurde. <!-- TODO: review code entity reference <xref:assetId:///E_FAIL?qualifyHint=False&amp;autoUpgrade=True>  -->E_FAIL wird zurückgegeben, wenn die Nachverfolgung nicht fortgesetzt werden kann, da der Kontext nicht verfügbar war.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** FileTracker.h  
  
## <a name="see-also"></a>Siehe auch  
 [SuspendTracking](../msbuild/suspendtracking.md)
