---
title: SccDirDiff Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccDirDiff
helpviewer_keywords:
- SccDirDiff function
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d2bea7816375da1131f557ebcbe206056f347f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138021"
---
# <a name="sccdirdiff-function"></a>SccDirDiff-Funktion
Diese Funktion zeigt die Unterschiede zwischen der aktuellen lokales Verzeichnis auf dem Datenträger des Clients und das entsprechende Projekt unter quellcodeverwaltung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpDirName  
 [in] Voll gekennzeichnete Pfad in das lokale Verzeichnis für das Anzeigen eines visuellen Unterschied.  
  
 dwFlags  
 [in] Befehl Flags (finden Sie unter "Hinweise" im Abschnitt).  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Das Verzeichnis auf dem Datenträger ist identisch mit dem Projekt im Quellcodeverwaltungssystem.|  
|SCC_I_FILESDIFFER|Das Verzeichnis auf dem Datenträger unterscheidet sich von dem Projekt im Quellcodeverwaltungssystem.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
|SCC_E_FILENOTCONTROLLED|Das Verzeichnis ist nicht unter quellcodeverwaltung.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischen Fehlers.|  
|SCC_E_FILENOTEXIST|Lokales Verzeichnis konnte nicht gefunden werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird verwendet, um anzuweisen, den Datenquellen-Steuerelement-Plug-In für den Benutzer eine Liste der Änderungen in einem angegebenen Verzeichnis anzuzeigen. Das plug-in wird in einem Format seiner Wahl, um die Unterschiede zwischen dem Verzeichnis des Benutzers auf dem Datenträger und das entsprechende Projekt unter Versionskontrolle anzuzeigen ein eigenen Fenster geöffnet.  
  
 Wenn einen Vergleich-Plug-in unterstützt alle Verzeichnisse, muss es Vergleich von Verzeichnissen auf Basis von Dateinamen unterstützen, auch wenn die Optionen "Quick-Diff" nicht unterstützt werden.  
  
|`dwFlags`|Interpretation|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Groß-und Kleinschreibung unterschieden (kann für die schnelle Diff oder Visualisierung verwendet werden).|  
|SCC_DIFF_IGNORESPACE|Ignoriert Leerraum (kann für Quick-Diff oder Visualisierung verwendet werden).|  
|SCC_DIFF_QD_CONTENTS|Wenn von der quellcodeverwaltung-Plug-in unterstützt, werden im Hintergrund im Verzeichnis byteweise verglichen.|  
|SCC_DIFF_QD_CHECKSUM|Wenn von-Plug-in unterstützt werden, im Hintergrund das Verzeichnis über eine Prüfsumme vergleicht oder, wenn nicht unterstützt, auf SCC_DIFF_QD_CONTENTS zurück fällt.|  
|SCC_DIFF_QD_TIME|Wenn von-Plug-in unterstützt, im Hintergrund das Verzeichnis mithilfe des Zeitstempels vergleicht oder, wenn nicht unterstützt, auf SCC_DIFF_QD_CHECKSUM oder SCC_DIFF_QD_CONTENTS zurück fällt.|  
  
> [!NOTE]
>  Diese Funktion verwendet die gleichen Befehlsflags als die [SccDiff](../extensibility/sccdiff-function.md). Ein Quellcodeverwaltungs-Plug-In können jedoch nicht den "Quick-" Vergleichsvorgang für Verzeichnisse unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)