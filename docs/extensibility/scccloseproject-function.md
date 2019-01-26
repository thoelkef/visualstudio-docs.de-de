---
title: SccCloseProject-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67f0a7ee44f948c46a77f17234b139b271b66d1b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947841"
---
# <a name="scccloseproject-function"></a>SccCloseProject-Funktion
Diese Funktion schließt ein Projekt, das das Ende einer bestimmten Sitzung markiert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
### <a name="parameters"></a>Parameter  
 pvContext  
 Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Das Projekt wurde erfolgreich geschlossen.|  
|SCC_E_PROJNOTOPEN|Es ist kein Projekt geöffnet.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler.|  
  
## <a name="remarks"></a>Hinweise  
 Die [SccOpenProject](../extensibility/sccopenproject-function.md) wird immer aufgerufen, bevor diese Funktion. Ein Aufruf dieser Funktion wird anschließend durch einen Aufruf an die `SccOpenProject` Funktion oder die [SccUninitialize](../extensibility/sccuninitialize-function.md), die beendet die Verbindung mit dem Quellcodeverwaltungssystem vollständig.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)