---
title: SccRemove-Funktion | Microsoft-Dokumentation
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
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b97e04c33b75dbee4fae4cd30f3de8a9aea3bd0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513637"
---
# <a name="sccremove-function"></a>SccRemove-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [SccRemove-Funktion](https://docs.microsoft.com/visualstudio/extensibility/sccremove-function).  
  
Diese Funktion löscht Dateien vom Quellcodeverwaltungssystem.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 nFiles  
 [in] Anzahl der angegebenen Dateien in die `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array der Namen von voll gekennzeichneter lokaler Pfad von Dateien, die entfernt werden soll.  
  
 lpComment  
 [in] Der Kommentar, der auf jede entfernte Datei angewendet werden.  
  
 Bestanden  
 [in] Befehl Flags (nicht verwendeten).  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Zum Entfernen war erfolgreich.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht unter quellcodeverwaltung.|  
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem wird dieser Vorgang nicht unterstützt.|  
|SCC_E_ISCHECKEDOUT|Eine Datei kann nicht entfernt werden, da ein Benutzer zurzeit ausgecheckt ist.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Datei wurde nicht entfernt.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion entfernt die Dateien aus dem Quellcodeverwaltungssystem, jedoch nicht von der Festplatte des Benutzers gelöscht.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)

