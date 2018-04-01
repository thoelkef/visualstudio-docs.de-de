---
title: SccGetExtendedCapabilities Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 16
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 870d793a11cccdaae9657deabb0e3b08c4d8c6f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities-Funktion
Diese Funktion gibt zusätzliche Funktionen, die von der quellcodeverwaltung-Plug-in unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 lSccExCaps  
 [in] Ein Kennzeichen, das eine erweiterte Funktion, der zu überprüfende angibt (siehe die Tabelle erweiterte Funktion Code im [Capability Flags](../extensibility/capability-flags.md) für die möglichen Flags).  
  
 pbSupported  
 [out] Ungleich 0 (null) zurückgibt (`TRUE`), wenn die angegebene Funktion unterstützt wird; gibt andernfalls 0 (null) (`FALSE`).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Vorgang des Get-Funktion, die erfolgreich abgeschlossen.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Unbekannter oder nicht angegebener Fehler ist aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird bei Bedarf aufgerufen wird. d. h., wenn eine Funktion werden getestet muss, wird diese Methode aufgerufen bestimmen, ob, die Funktion unterstützt wird. Nur ein Flag zu einem Zeitpunkt angegeben ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Fehlercodes](../extensibility/error-codes.md)   
 [Funktionsflags](../extensibility/capability-flags.md)