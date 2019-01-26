---
title: SccUncheckout-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: acded327d8e1b5b1b2bec0b804e6e72ac157be1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950571"
---
# <a name="sccuncheckout-function"></a>SccUncheckout-Funktion
Diese Funktion macht eine vorherige Auscheckvorgang, wiederherstellen und den Inhalt der ausgewählten Datei oder Dateien in den Zustand vor dem Auschecken rückgängig. Alle in die Datei seit dem Auschecken vorgenommene Änderungen gehen verloren.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccUncheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 nFiles  
 [in] Anzahl der angegebenen Dateien in die `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array der Namen von voll gekennzeichneter lokaler Pfad von Dateien für das Auschecken rückgängig gemacht.  
  
 Bestanden  
 [in] Befehls-Flags (nicht verwendet).  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|"Auschecken rückgängig" war erfolgreich.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht unter quellcodeverwaltung befindet.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler. Rückgängig: Auschecken nicht erfolgreich war.|  
|SCC_E_NOTCHECKEDOUT|Der Benutzer besitzt nicht die Datei ausgecheckt haben.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht aus der quellcodeverwaltung geöffnet.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|  
  
## <a name="remarks"></a>Hinweise  
 Nach diesem Vorgang die `SCC_STATUS_CHECKEDOUT` und `SCC_STATUS_MODIFIED` Flags werden sowohl für die Dateien auf dem die "Auschecken rückgängig" ausgeführt wurde gelöscht werden.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)