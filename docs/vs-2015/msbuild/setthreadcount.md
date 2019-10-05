---
title: SetThreadCount | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- SetThreadCount
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 79987c77da7959c4ba37a4ae8e5b689a052cbbbc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193641"
---
# <a name="setthreadcount"></a>SetThreadCount
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Legt die Anzahl der globalen Threads fest, und weist diese Anzahl für dem aktuellen Thread zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in] `threadCount`  
 Die Anzahl der zu verwendenden Threads.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [HRESULT])<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) mit der [erfolgreich] ()<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->)-Bit festgelegt ist, wenn die Anzahl der Threads aktualisiert wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** FileTracker.h
