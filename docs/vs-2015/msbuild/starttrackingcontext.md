---
title: StartTrackingContext| Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 4a99059dbfdde4a8d00d65796a978fc65278ee43
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306565"
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
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) mit dem [erfolgreich] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->)-Bit festgelegt ist, wenn der Nachverfolgungskontext erstellt wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** FileTracker.h



