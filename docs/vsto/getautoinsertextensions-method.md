---
title: GetAutoInsertExtensions-Methode | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1d222f7b6751381ceb4ebdb27bb6a6bf223616df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions-Methode
  Ruft Informationen zu den apps für Office, die während des Debuggens automatisch eingefügt werden sollen.  
  
 Diese Methode ist für eine spätere Verwendung vorgesehen.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*psaExtensionNames*|Die Erweiterungsnamen der apps für Office.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.  
  
## <a name="remarks"></a>Hinweise  
 Jede app für Office einzufügenden wird als einen Erweiterungsnamen der Office-Anwendung zurückgegeben, die auf einen Wert unter HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer entspricht. Der Host muss diese Werte in der Registrierung suchen, und fügen Sie dann die Erweiterungen automatisch.  
  
  