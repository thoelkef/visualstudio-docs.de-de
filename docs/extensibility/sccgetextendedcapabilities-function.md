---
title: SccGetExtendedCapabilities-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c46a81190fb1c1c9b15627b7fb9620e01faa2f53
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819598"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities-Funktion
Diese Funktion gibt die zusätzliche Funktionen, die von das Quellcodeverwaltungs-Plug-in unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.  
  
 lSccExCaps  
 [in] Ein Flag, das eine erweiterte Funktion, die zu überprüfende angibt (siehe die Tabelle erweiterte Funktion Code im [funktionsflags](../extensibility/capability-flags.md) für die möglichen Flags).  
  
 pbSupported  
 [out] Ungleich NULL zurück (`TRUE`) Wenn die angegebene Funktion unterstützt wird; andernfalls wird NULL (`FALSE`).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Vorgang des Get-Funktion, die erfolgreich abgeschlossen.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Unbekannte oder nicht angegebene Fehler ist aufgetreten.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird bei Bedarf aufgerufen. also wenn eine Funktion getestet werden muss, wird diese Methode aufgerufen, um zu bestimmen, ob, die Funktion unterstützt wird. Nur ein Flag zu einem Zeitpunkt angegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Fehlercodes](../extensibility/error-codes.md)   
 [Funktionsflags](../extensibility/capability-flags.md)