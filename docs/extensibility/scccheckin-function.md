---
title: SccCheckin Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf8c8d23a89e55b272657dde0c2374c78e63bfaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138853"
---
# <a name="scccheckin-function"></a>SccCheckin-Funktion
Diese Funktion überprüft in zuvor ausgecheckten Dateien auf dem Quellcodeverwaltungssystem, speichern die Änderungen und Erstellen einer neuen Version. Diese Funktion wird mit einer Anzahl und ein Array von Namen der Dateien eingecheckt werden aufgerufen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das die SCC-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 [in] Die Anzahl der Dateien, die eingecheckt werden ausgewählt.  
  
 lpFileNames  
 [in] Array der Namen von voll gekennzeichneter lokaler Pfad von Dateien eingecheckt werden kann.  
  
 lpComment  
 [in] Kommentar an, der auf jedem der ausgewählten eingecheckten Dateien angewendet werden. Dies ist `NULL` das Quellsteuerelement-Plug-In für einen Kommentar Fragen sollen.  
  
 fOptions  
 [in] Befehl Flags, die entweder 0 oder `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] SCC-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Dateien wurde erfolgreich aktiviert.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht unter quellcodeverwaltung.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers. Datei wurde nicht eingecheckt.|  
|SCC_E_NOTCHECKEDOUT|Der Benutzer hat die Datei, sodass sie nicht Einchecken nicht ausgecheckt.|  
|SCC_E_CHECKINCONFLICT|Einchecken konnte nicht ausgeführt werden, da:<br /><br /> -Ein anderer Benutzer im Voraus eingecheckt hat und `bAutoReconcile` wurde "false".<br /><br /> - oder - <br /><br /> – Die automatische Zusammenführung kann nicht erfolgen, (z. B., wenn die Dateien binär sind).|  
|SCC_E_VERIFYMERGE|Datei automatisch zusammengeführt wurde, aber nicht eingecheckt wurde ausstehende Überprüfung des Benutzers.|  
|SCC_E_FIXMERGE|Datei automatisch zusammengeführt wurde, jedoch nicht in eingecheckt wurde aufgrund eines Mergekonflikts, das manuell behoben werden muss.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_I_OPERATIONCANCELED|Vorgang wurde vor dem Abschluss abgebrochen.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
|SCC_E_FILENOTEXIST|Lokale Datei wurde nicht gefunden.|  
  
## <a name="remarks"></a>Hinweise  
 Der Kommentar gilt für alle eingecheckten Dateien. Das Kommentar-Argument kann eine `null` "string", in diesem Fall kann das Quellsteuerelement-Plug-in der Benutzer für einen Kommentar für jede Datei auffordern.  
  
 Die `fOptions` Argument kann einen Wert zugewiesen werden die `SCC_KEEP_CHECKEDOUT` Flag zur Angabe der Benutzer versucht, die Datei einchecken und probieren Sie es erneut.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)