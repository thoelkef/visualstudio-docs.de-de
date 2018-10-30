---
title: SccGetUserOption-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40832984886aeb96e0a58279ef1c91c352b7c1c9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853817"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [out] Option zugeordnete Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Option wurde erfolgreich abgerufen.|  
|SCC_E_OPNOTSUPPORTED|Option wird nicht unterstützt.|  
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Die folgenden Optionen werden von dieser Befehl unterstützt:  
  
|Benutzeroption|Beschreibung|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Bestimmt, ob der Benutzer möchte auf die lokale Version von Dateien auszuchecken. `lpVal` erhält `SCC_USEROPT_COLV_YES` (möchte Benutzer lokale Dateien auschecken) oder `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Fehlercodes](../extensibility/error-codes.md)

