---
title: SccInitialize Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1146573f3d969ffc5cd56576ba92faa4e6ffdce0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccinitialize-function"></a>SccInitialize-Funktion
Diese Funktion initialisiert den Datenquellen-Steuerelement-Plug-in und enthält Funktionen und Beschränkungen für die integrierte Entwicklungsumgebung (IDE).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [in] Die Datenquellen-Steuerelement-Plug-in kann einen Zeiger auf die Kontextstruktur hier platzieren.  
  
 `hWnd`  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 `lpCallerName`  
 [in] Der Name des Programms das Quellsteuerelement-Plug-in aufrufen.  
  
 `lpSccName`  
 [in, out] Der Puffer, in dem das Quellsteuerelement-Plug-in einen eigenen Namen setzt (nicht zu überschreiten `SCC_NAME_LEN`).  
  
 `lpSccCaps`  
 [out] Gibt die Datenquellen-Steuerelement-Plug-ins Funktion Flags zurück.  
  
 `lpAuxPathLabel`  
 [in, out] Der Puffer, in dem das Quellsteuerelement-Plug-in setzt eine Zeichenfolge, die beschreibt, die `lpAuxProjPath` zurückgegebenes Parameter der [SccOpenProject](../extensibility/sccopenproject-function.md) und [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (nicht zu überschreiten `SCC_AUXLABEL_LEN`).  
  
 `pnCheckoutCommentLen`  
 [out] Gibt die maximale zulässige Länge für einen Auscheckkommentar.  
  
 `pnCommentLen`  
 [out] Gibt die maximale zulässige Länge für andere Kommentare zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Source Control Initialisierung erfolgreich beendet.|  
|SCC_E_INITIALIZEFAILED|System konnte nicht initialisiert werden.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um den angegebenen Vorgang auszuführen.|  
|SCC_E_NONSPECFICERROR|Unspezifischen Fehlers; Quellcodeverwaltungssystem wurde nicht initialisiert.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE ruft diese Funktion beim ersten der Datenquellen-Steuerelement-Plug-In laden. Dadurch werden der IDE an, um bestimmte Informationen, z. B. der Name vom Aufrufer an das plug-in übergeben. Die IDE ruft auch wieder bestimmte Informationen wie z. B. die maximal zulässige Länge für Kommentare und das Plug-in Funktionen.  
  
 Die `ppvContext` verweist auf eine `NULL` Zeiger. Das Quellsteuerelement-Plug-in kann eine Struktur für die eigene Verwendung zuordnen und speichern Sie einen Zeiger auf dieser Struktur in `ppvContext`. Die IDE übergibt this-Zeiger an jede andere VSSCI-API-Funktion ermöglicht das plug-in Kontextinformationen zur Verfügung zu haben, ohne globalen Speicher und Unterstützung für mehrere Instanzen des Plug-Ins. Diese Struktur sollte aufgehoben werden, wenn die [SccUninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.  
  
 Die `lpCallerName` und `lpSccName` Typparameter ermöglichen es der IDE und die Datenquellen-Steuerelement-Plug-In für den Nachrichtenaustausch Namen. Diese Namen können einfach, zur Unterscheidung zwischen mehreren Instanzen verwendet werden, oder sie möglicherweise tatsächlich in Menüs oder Dialogfeldern angezeigt.  
  
 Die `lpAuxPathLabel` Parameter ist eine Zeichenfolge, die als Kommentar verwendet werden, um den zusätzlichen Projektpfad zu identifizieren, die in der Projektmappendatei gespeichert und übergeben das Quellsteuerelement-Plug-in in einem Aufruf der [SccOpenProject](../extensibility/sccopenproject-function.md). [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] die Zeichenfolge "SourceSafe-Projekt:"; andere Datenquellen-Steuerelement-Plug-ins muss mit dieser bestimmten Zeichenfolge fest.  
  
 Die `lpSccCaps` Parameter enthält das Quellsteuerelement-Plug-in einen Ort zum Speichern von Bitflags, der angibt, das Plug-in Funktionen. (Eine vollständige Liste der Funktion Bitflags finden Sie unter [Capability Flags](../extensibility/capability-flags.md)). Für die Instanz, wenn die Plug-in-Pläne, Ergebnisse in eine Rückruffunktion vom Aufrufer bereitgestellter zu schreiben, das plug-in legen die Funktion SCC_CAP_TEXTOUT bit. Dies würde die IDE beim Erstellen eines Fensters für Version Steuerelement Ergebnisse zu signalisieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [Funktionsflags](../extensibility/capability-flags.md)