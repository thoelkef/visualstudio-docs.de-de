---
title: SetThreadCount | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: e6d9e8e107d4935b8de659dc40f60ccaa7831def
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514252"
---
# <a name="setthreadcount"></a>SetThreadCount
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SetThreadCount](https://docs.microsoft.com/visualstudio/msbuild/setthreadcount).  
  
  
Legt die Anzahl der globalen Threads fest, und weist diese Anzahl für dem aktuellen Thread zu.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in] `threadCount`  
 Die Anzahl der zu verwendenden Threads.  
  
## <a name="return-value"></a>Rückgabewert  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) mit dem [erfolgreich] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->)-Bit festgelegt ist, wenn die Anzahl der Threads aktualisiert wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** FileTracker.h



