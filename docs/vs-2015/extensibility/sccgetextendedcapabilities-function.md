---
title: SccGetExtendedCapabilities-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 016b44e8dcd8218b8c3fbd569ba6a27b77d9d204
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516197"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SccGetExtendedCapabilities-Funktion](https://docs.microsoft.com/visualstudio/extensibility/sccgetextendedcapabilities-function).  
  
Diese Funktion gibt die zusätzliche Funktionen, die von das Quellcodeverwaltungs-Plug-in unterstützt werden.  
  
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
 [in] Ein Flag, das eine erweiterte Funktion, die zu überprüfende angibt (siehe die Tabelle erweiterte Funktion Code im [Capability Flags](../extensibility/capability-flags.md) für die Flags möglich).  
  
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
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [Fehlercodes](../extensibility/error-codes.md)   
 [Funktionsflags](../extensibility/capability-flags.md)

