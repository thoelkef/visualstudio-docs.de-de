---
title: SccCloseProject Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f977c1241408f5e33d31a63262abb5ee24670e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="scccloseproject-function"></a>SccCloseProject-Funktion
Diese Funktion wird ein Projekt, markiert das Ende einer bestimmten Sitzung geschlossen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Das Projekt wurde erfolgreich geschlossen.|  
|SCC_E_PROJNOTOPEN|Kein Projekt ist derzeit geöffnet.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers.|  
  
## <a name="remarks"></a>Hinweise  
 Die [SccOpenProject](../extensibility/sccopenproject-function.md) wird immer aufgerufen, bevor diese Funktion. Ein Aufruf dieser Funktion wird gefolgt von einem Aufruf von der `SccOpenProject` Funktion oder die [SccUninitialize](../extensibility/sccuninitialize-function.md), die die Verbindung mit dem Quellcodeverwaltungssystem vollständig beendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)