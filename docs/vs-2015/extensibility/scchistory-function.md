---
title: SccHistory-Funktion | Microsoft-Dokumentation
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
- SccHistory
helpviewer_keywords:
- SccHistory function
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3a01e3d854b2527a38595509699aa94a222a9ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522597"
---
# <a name="scchistory-function"></a>SccHistory-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SccHistory-Funktion](https://docs.microsoft.com/visualstudio/extensibility/scchistory-function).  
  
Diese Funktion zeigt den Verlauf der angegebenen Dateien.  
  
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
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 `hWnd`  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 `nFiles`  
 [in] Anzahl der angegebenen Dateien in die `lpFileName` Array.  
  
 `lpFileName`  
 [in] Array von vollqualifizierten Namen von Dateien.  
  
 `fOptions`  
 [in] Befehls-Flags (zurzeit nicht verwendet).  
  
 `pvOptions`  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Versionsverlauf wurde erfolgreich abgerufen.|  
|SCC_I_RELOADFILE|Das Quellcodeverwaltungssystem tatsächlich Datei auf dem Datenträger geändert, beim Abrufen des Verlaufs (beispielsweise durch Abrufen einer alten Version davon), damit die IDE die Datei neu geladen werden soll.|  
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht unter quellcodeverwaltung.|  
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem wird dieser Vorgang nicht unterstützt.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht geöffnet.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler. Der Dateiversionsverlauf konnte nicht abgerufen werden.|  
  
## <a name="remarks"></a>Hinweise  
 Das Quellcodeverwaltungs-Plug-in kann ein eigenes Dialogfeld, um den Verlauf jeder Datei anzeigen Anzeigen mit `hWnd` als übergeordnetes Fenster. Alternativ Ausgabe von der optionale Text Rückruf Funktion angegeben wird, um die [SccOpenProject](../extensibility/sccopenproject-function.md) kann verwendet werden, wenn dies unterstützt wird.  
  
 Beachten Sie, dass unter bestimmten Umständen die untersuchte Datei während der Ausführung dieses Aufrufs ändern kann. Z. B. die [!INCLUDE[vsvss](../includes/vsvss-md.md)] History-Befehl gibt dem Benutzer die Möglichkeit, die eine alte Version der Datei zu erhalten. In diesem Fall die Quellcode-Plug-Ins gibt `SCC_I_RELOAD` um der IDE zu warnen, dass die Datei neu geladen werden muss.  
  
> [!NOTE]
>  Wenn das Quellcodeverwaltungs-Plug-in diese Funktion nicht für ein Array von Dateien unterstützt, kann nur der Dateiversionsverlauf für die erste Datei angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungsfunktionen-Plug-in-API](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)

