---
title: 'Iactivescriptsitewindow:: GetWindow | Microsoft-Dokumentation'
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
ms.openlocfilehash: d8263db447c7692ec7b0982127d63b4bea588a4b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574356"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Ruft das Handle für ein Fenster ab, das als Besitzer eines Popup Fensters fungieren kann, das von der Skript-Engine angezeigt werden muss.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phwnd`  
 vorgenommen Adresse einer Variablen, die das Fenster Handle empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_FAIL`, wenn ein Fehler aufgetreten ist.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ähnelt der `IOleWindow::GetWindow`-Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)