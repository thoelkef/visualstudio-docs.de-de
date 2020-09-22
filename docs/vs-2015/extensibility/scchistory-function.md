---
title: Scchistory-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8df85c03201e46768c43fb64cc41b7fa081eb91a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840919"
---
# <a name="scchistory-function"></a>SccHistory-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion zeigt den Verlauf der angegebenen Dateien an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccHistory(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pvContext`  
 in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.  
  
 `hWnd`  
 in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.  
  
 `nFiles`  
 in Anzahl der im Array angegebenen Dateien `lpFileName` .  
  
 `lpFileName`  
 in Array von voll qualifizierten Namen von Dateien.  
  
 `fOptions`  
 in Befehlsflags (derzeit nicht verwendet).  
  
 `pvOptions`  
 in Plug-in-spezifische Optionen für die Quell Code Verwaltung.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Der Versionsverlauf wurde erfolgreich abgerufen.|  
|SCC_I_RELOADFILE|Das Quell Code Verwaltungssystem änderte die Datei auf dem Datenträger, während der Verlauf abgerufen wurde (z.b. durch Abrufen einer alten Version), sodass die IDE diese Datei erneut laden sollte.|  
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|  
|SCC_E_OPNOTSUPPORTED|Das Quell Code Verwaltungssystem unterstützt diesen Vorgang nicht.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|  
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht geöffnet.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler. Der Datei Versionsverlauf konnte nicht abgerufen werden.|  
  
## <a name="remarks"></a>Bemerkungen  
 Das Quellcodeverwaltungs-Plug-in kann ein eigenes Dialogfeld anzeigen, in dem der Verlauf der einzelnen Dateien angezeigt wird, wobei `hWnd` als übergeordnetes Fenster verwendet wird. Alternativ kann die optionale, für das [sccopenproject](../extensibility/sccopenproject-function.md) bereitgestellte Textausgabe-Rückruffunktion verwendet werden, sofern diese unterstützt wird.  
  
 Beachten Sie, dass sich die Datei, die unter bestimmten Umständen überprüft wird, während der Ausführung dieses Aufrufes ändern kann. Der [!INCLUDE[vsvss](../includes/vsvss-md.md)] Verlaufs Befehl gibt dem Benutzer beispielsweise die Möglichkeit, eine alte Version der Datei zu erhalten. In einem solchen Fall gibt das Quellcodeverwaltungs-Plug-in zurück, `SCC_I_RELOAD` um die IDE zu warnen, dass Sie die Datei erneut laden muss.  
  
> [!NOTE]
> Wenn das Quellcodeverwaltungs-Plug-in diese Funktion für ein Array von Dateien nicht unterstützt, kann nur der Datei Versionsverlauf für die erste Datei angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)
