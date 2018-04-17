---
title: SccGetUserOption Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b735b8ae53ef484417ae007c6ec74ec03fe4b849
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption-Funktion
Diese Funktion ruft eine Vielzahl von benutzerspezifischen Optionen ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 nOption  
 [in] Option zum Abrufen (mögliche Optionen finden Sie unter "Hinweise").  
  
 lpVal  
 [out] Der Wert für Option zugeordnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Option wurde erfolgreich abgerufen.|  
|SCC_E_OPNOTSUPPORTED|Option wird nicht unterstützt.|  
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Mit diesem Befehl werden die folgenden Optionen unterstützt:  
  
|Benutzeroption|Beschreibung|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Bestimmt, ob der Benutzer möchte lokale Version von Dateien auszuchecken. `lpVal` wird zugewiesen `SCC_USEROPT_COLV_YES` (Benutzer möchte zum Auschecken von lokaler Dateien) oder `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Fehlercodes](../extensibility/error-codes.md)