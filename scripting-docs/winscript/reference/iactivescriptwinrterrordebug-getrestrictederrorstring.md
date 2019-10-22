---
title: 'Iactivescriptwinrterrordebug:: getrestrictederrorstring | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 498d929fb06eea1d6717bfdecb09107bbdaafd98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577903"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorstring"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
Gibt den Windows-Runtime eingeschränkten Fehler Zeichenfolge zurück, falls verfügbar.  
  
> [!IMPORTANT]
> Die [iactivescriptwinrterrordebug-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) wird von PDM v 11.0 und höher implementiert. Gefunden in activdbg100.h.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);   
```  
  
#### <a name="parameters"></a>Parameter  
 `errorString`  
 vorgenommen Die eingeschränkte Fehler Zeichenfolge.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptWinRTErrorDebug-Schnittstelle](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)