---
title: SccInitialize-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ce52b65d028f82d75d4890b0b1298b4d13b7eafa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200034"
---
# <a name="sccinitialize-function"></a>SccInitialize-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion initialisiert das Quellcodeverwaltungs-Plug-in und enthält Funktionen und Einschränkungen, die integrierte Entwicklungsumgebung (IDE).  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppvContext`  
 [in] Das Quellcodeverwaltungs-Plug-in kann einen Zeiger auf die Context-Struktur hier platzieren.  
  
 `hWnd`  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 `lpCallerName`  
 [in] Der Name des Programms das Quellcodeverwaltungs-Plug-in aufrufen.  
  
 `lpSccName`  
 [in, out] Der Puffer, in dem das Quellcodeverwaltungs-Plug-in einen eigenen Namen setzt (nicht zu überschreiten `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Gibt das Quellcodeverwaltungs-Plug-ins funktionsflags zurück.  
  
 `lpAuxPathLabel`  
 [in, out] Der Puffer, in dem das Quellcodeverwaltungs-Plug-in Fügt eine Zeichenfolge, die beschreibt, die `lpAuxProjPath` Parameter zurückgegeben werden, indem die [SccOpenProject](../extensibility/sccopenproject-function.md) und [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (, nicht zu überschreiten `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Gibt die maximale zulässige Länge für eine Auscheckkommentar zurück.  
  
 `pnCommentLen`  
 [out] Gibt die maximale zulässige Länge für andere Kommentare zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Source-Control-Initialisierung erfolgreich beendet.|  
|SCC_E_INITIALIZEFAILED|System konnte nicht initialisiert werden.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um den angegebenen Vorgang auszuführen.|  
|SCC_E_NONSPECFICERROR|Unspezifischen Fehlers; Quellcode-Verwaltungssystems wurde nicht initialisiert.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE ruft diese Funktion auf, wenn zuerst das Quellcodeverwaltungs-Plug-In geladen. Dadurch wird die IDE, um bestimmte Informationen, z. B. den Namen des Aufrufers an, an das plug-in übergeben. Die IDE zurückerhält auch bestimmte Informationen, z.B. die maximal zulässige Länge für Kommentare und das Plug-in Funktionen.  
  
 Die `ppvContext` verweist auf eine `NULL` Zeiger. Das Quellcodeverwaltungs-Plug-in eine Struktur zur eigenen Verwendung zuordnen kann, und speichern Sie einen Zeiger auf dieser Struktur in `ppvContext`. Die IDE übergibt this-Zeiger auf jede andere VSSCI-API-Funktion ermöglicht das plug-in, das Kontextinformationen zur Verfügung zu haben, ohne in den globalen Speicher und Unterstützung für mehrere Instanzen des Plug-Ins. Diese Struktur sollte aufgehoben werden, wenn die [SccUninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.  
  
 Die `lpCallerName` und `lpSccName` Parameter ermöglichen die IDE und das Quellcodeverwaltungs-Plug-in zum Austauschen von Namen. Diese Namen können verwendet werden, um zwischen mehreren Instanzen unterscheiden zu können, oder diese in Menüs oder Dialogfelder tatsächlich auftreten.  
  
 Die `lpAuxPathLabel` Parameter ist eine Zeichenfolge, die als Kommentar verwendet, um den zusätzlichen Projektpfad zu identifizieren, die in der Projektmappendatei gespeichert und an das Quellcodeverwaltungs-Plug-in in einem Aufruf übergeben die [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../includes/vsvss-md.md)] verwendet die Zeichenfolge "SourceSafe-Projekt:"; andere Quellcodeverwaltungs-Plug-ins sollte nicht zu dieser Zeichenfolge verwenden.  
  
 Die `lpSccCaps` Parameter enthält das Quellcodeverwaltungs-Plug-in einen Ort zum Speichern von Bitflags, der angibt, das Plug-in Funktionen. (Eine vollständige Liste der Funktion Bitflags, finden Sie unter [Capability Flags](../extensibility/capability-flags.md)). Beispielsweise, wenn die Plug-in-Pläne, Ergebnisse in eine vom Aufrufer bereitgestellter Callback-Funktion zu schreiben, das plug-in wird die Funktion festgelegt SCC_CAP_TEXTOUT bit. Dies würde die IDE zum Erstellen eines Fensters für Version Steuerelement führt zu signalisieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Funktionsflags](../extensibility/capability-flags.md)
