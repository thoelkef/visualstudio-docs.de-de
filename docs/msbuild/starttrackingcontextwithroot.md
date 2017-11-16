---
title: StartTrackingContextWithRoot | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StartTrackingContextWithRoot
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 0d49543bde0195144fb4918e9a9f173f8f9435ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
Startet einen Nachverfolgungskontext mithilfe einer Antwortdatei, die einen Stammmarker angibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp 
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Parameter  
 [in] `intermediateDirectory`  
 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll  
  
 [in] `taskName`  
 Identifiziert den Nachverfolgungskontext. Dieser Name wird verwendet, um den Protokolldateinamen zu erstellen.  
  
 [in] `rootMarkerResponseFile`  
 Der Pfadname einer Antwortdatei mit einem Stammmarker. Der Stammname wird verwendet, um alle Nachverfolgungen für einen Kontext zusammen zu gruppieren.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **HRESULT**, bei dem **SUCCEEDED** festgelegt ist, wenn der Nachverfolgungskontext erstellt wurde  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** FileTracker.h  
  
## <a name="see-also"></a>Siehe auch  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)