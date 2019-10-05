---
title: StartTrackingContext| Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContext
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da002fe757d623a665b39c16cc10e77e492e2660
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199931"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Starten eines Nachverfolgungskontexts.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in] `intermediateDirectory`  
 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll  
  
 [in] `taskName`  
 Identifiziert den Nachverfolgungskontext. Dieser Name wird verwendet, um den Protokolldateinamen zu erstellen.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [HRESULT])<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) mit der [erfolgreich] ()<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->)-Bit festgelegt ist, wenn der Nachverfolgungskontext erstellt wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** FileTracker.h
