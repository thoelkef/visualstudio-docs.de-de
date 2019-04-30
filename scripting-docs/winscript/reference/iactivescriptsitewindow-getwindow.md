---
title: IActiveScriptSiteWindow::GetWindow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b6efa066765339375a8315695aa9c1de2f9c46b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992073"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Ruft das Handle für ein Fenster, das als Besitzer eines Popupfensters fungieren kann, die die Skript-Engine angezeigt werden muss.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phwnd`  
 [out] Die Adresse einer Variablen, die das Fensterhandle empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` , wenn ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ähnelt der `IOleWindow::GetWindow` Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)