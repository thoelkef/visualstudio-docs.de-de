---
title: Scccloseproject-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156139"
---
# <a name="scccloseproject-function"></a>SccCloseProject-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion schließt ein Projekt und markiert das Ende einer bestimmten Sitzung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvcontext  
 Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Das Projekt wurde erfolgreich geschlossen.|  
|SCC_E_PROJNOTOPEN|Zurzeit ist kein Projekt geöffnet.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|  
  
## <a name="remarks"></a>Bemerkungen  
 Das [sccopenproject](../extensibility/sccopenproject-function.md) wird immer vor dieser Funktion aufgerufen. Auf einen aufzurufenden Befehl folgt entweder die- `SccOpenProject` Funktion oder die [sccuninitialize](../extensibility/sccuninitialize-function.md)-Funktion, die die Verbindung mit dem Quell Code Verwaltungssystem vollständig beendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [Sccopumproject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
