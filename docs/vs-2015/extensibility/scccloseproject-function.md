---
title: SccCloseProject-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156139"
---
# <a name="scccloseproject-function"></a>SccCloseProject-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion schließt ein Projekt, das das Ende einer bestimmten Sitzung markiert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
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
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
