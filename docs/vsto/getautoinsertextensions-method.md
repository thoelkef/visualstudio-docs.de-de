---
title: GetAutoInsertExtensions-Methode | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67f6bfcb0ee38acf9abb604f28fa95eeaa605fde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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
  
  