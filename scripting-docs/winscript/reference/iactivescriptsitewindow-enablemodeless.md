---
title: IActiveScriptSiteWindow::EnableModeless | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7099fe7d13a1cb3231e67049104722af9373d7a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Bewirkt, dass den Host zum Aktivieren oder deaktivieren das Hauptfenster als auch für alle nicht modale Dialogfelder.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fEnable`  
 [in] Wenn ein Flag, das `TRUE`, ermöglicht das Hauptfenster und nicht modale Dialogfelder oder, wenn der `FALSE`, deaktiviert sie.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` bei einem Fehler.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist identisch mit der `IOleInPlaceFrame::EnableModeless` Methode.  
  
 Aufrufe dieser Methode können geschachtelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)