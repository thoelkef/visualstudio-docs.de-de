---
title: SccHistory Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 464c71d7caeca1b9b8c4c3455dad1737649f5ea4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138199"
---
# <a name="scchistory-function"></a>SccHistory-Funktion
Diese Funktion zeigt den Verlauf der angegebenen Dateien an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 `hWnd`  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 `nFiles`  
 [in] Anzahl der angegebenen Dateien in den `lpFileName` Array.  
  
 `lpFileName`  
 [in] Array von vollqualifizierten Namen von Dateien.  
  
 `fOptions`  
 [in] Befehl Flags (zurzeit nicht verwendet).  
  
 `pvOptions`  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Verlauf-Version wurde erfolgreich abgerufen.|  
|SCC_I_RELOADFILE|Vom Quellcodeverwaltungssystem tatsächlich Datei auf dem Datenträger geändert, beim Abrufen des Verlaufs (z. B. durch Abrufen des Zertifikats einer alten Version), damit die IDE diese Datei neu geladen werden soll.|  
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht in der quellcodeverwaltung.|  
|SCC_E_OPNOTSUPPORTED|Dieser Vorgang wird von das Quellcodeverwaltungssystem nicht unterstützt.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht geöffnet.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers. Dateiversionsverlauf konnte nicht abgerufen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Die Datenquellen-Steuerelement-Plug-in kann ein eigenes Dialogfeld, um den Verlauf jeder Datei anzeigen Anzeigen mit `hWnd` als das übergeordnete Fenster. Alternativ können Sie der optionale Text Rückruf Ausgabe Funktion angegeben wird, um die [SccOpenProject](../extensibility/sccopenproject-function.md) können verwendet werden, wenn es unterstützt wird.  
  
 Beachten Sie, dass unter bestimmten Umständen ist die Datei, die überprüft wird während der Ausführung dieses Aufrufs ändern kann. Z. B. die [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] History-Befehl hat dem Benutzer die Möglichkeit, eine alte Version der Datei zu erhalten. In diesem Fall die Quelle-Plug-Ins gibt steuern `SCC_I_RELOAD` , der IDE hinweist, dass die Datei neu geladen werden muss.  
  
> [!NOTE]
>  Wenn die Datenquellen-Steuerelement-Plug-in diese Funktion nicht für ein Array von Dateien unterstützt, kann nur der Dateiversionsverlauf für die erste Datei angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)