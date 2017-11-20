---
title: SccRemove Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccRemove
helpviewer_keywords: SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 28901d9635a4a823507834cde201860fda1e2168
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="sccremove-function"></a>SccRemove-Funktion
Diese Funktion werden Dateien aus dem Quellcodeverwaltungssystem gelöscht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 [in] Anzahl der angegebenen Dateien in den `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array der Namen von voll gekennzeichneter lokaler Pfad von Dateien entfernt werden soll.  
  
 lpComment  
 [in] Der Kommentar auf jede Datei entfernten angewendet werden soll.  
  
 fOptions  
 [in] Befehl Flags (nicht verwendet wird).  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Deinstallation war erfolgreich.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht in der quellcodeverwaltung.|  
|SCC_E_OPNOTSUPPORTED|Dieser Vorgang wird von das Quellcodeverwaltungssystem nicht unterstützt.|  
|SCC_E_ISCHECKEDOUT|Eine Datei kann nicht entfernt werden, da ein Benutzer derzeit ausgecheckt wurde.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Datei wurde nicht entfernt.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion entfernt die Dateien aus dem Quellcodeverwaltungssystem jedoch nicht aus der lokalen Festplatte des Benutzers gelöscht.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)