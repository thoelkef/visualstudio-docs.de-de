---
title: 'Iactivescriptsitewindow:: enablemodeless | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 756bda6209b6209ff14f6d67fef18faaed0b5618
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574130"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Bewirkt, dass der Host sein Hauptfenster sowie alle nicht modalem Dialogfelder aktiviert oder deaktiviert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `fEnable`  
 in Flag, `TRUE` das das Hauptfenster und die nicht modaldialog Feld-Dialogfeld aktiviert oder, wenn `FALSE`, deaktiviert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_FAIL`, wenn ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist identisch mit der `IOleInPlaceFrame::EnableModeless`-Methode.  
  
 Aufrufe dieser Methode können eingebettet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)