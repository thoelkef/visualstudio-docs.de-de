---
title: GetAutoInsertExtensions-Methode
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a12adf6e83e58b877e36dd65d98b617cda3a39b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647209"
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions-Methode
  Ruft Informationen zu den apps für Office, die während des Debuggens automatisch eingefügt werden sollen.  
  
 Diese Methode ist für eine spätere Verwendung vorgesehen.  
  
## <a name="syntax"></a>Syntax  
  
```csharp
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*psaExtensionNames*|Die Erweiterungsnamen der apps für Office.|  
  
## <a name="return-value"></a>Rückgabewert  
 Ein HRESULT-Wert, der angibt, ob die Methode erfolgreich abgeschlossen wurde.  
  
## <a name="remarks"></a>Hinweise  
 Jede app für Office, eingefügt werden soll, wird als Office-Erweiterung Anwendungsname, der einen Wert unter entspricht zurückgegeben **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Der Host muss diese Werte in der Registrierung nachschlagen, und fügen Sie dann die Erweiterungen automatisch.  
  
  