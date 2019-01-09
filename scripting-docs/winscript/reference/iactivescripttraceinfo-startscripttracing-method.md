---
title: 'Iactivescripttraceinfo:: Startscripttracing-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6462597f55b6b0ceee885d207572e9669a350600
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093640"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing-Methode
Startet die Ablaufverfolgung von Skripts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>Parameter  
 `pSiteTraceInfo`  
 Ein Zeiger auf die Hosts IActiveScriptSiteTraceInfo.  
  
 `guidContextId`  
 Die GUID des Kontexts.  
  
## <a name="return-value"></a>Rückgabewert  
 Die möglichen Rückgabewerte für diese Methode sind folgende:  
  
1.  S_OK: Erfolgreich.  
  
2.  E_POINTER: `pSiteTraceInfo` ist ein Nullzeiger.  
  
3.  E_NOTIMPL: Nicht implementiert.