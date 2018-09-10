---
title: SccDirDiff-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 697139499678814b4e4d6d360c42ed6d37bfd1e4
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636203"
---
# <a name="sccdirdiff-function"></a>SccDirDiff-Funktion
Diese Funktion zeigt die Unterschiede zwischen der aktuellen lokalen Verzeichnis auf dem Client-Datenträger und das entsprechende Projekt unter quellcodeverwaltung.  
  
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
  
### <a name="parameters"></a>Parameter  
 "pContext"  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 lpDirName  
 [in] Den vollqualifizierten Pfad zum lokalen Verzeichnis für das Anzeigen eines visuellen Unterschied.  
  
 dwFlags  
 [in] Befehl Flags (finden Sie unter "Hinweise" im Abschnitt).  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Das Verzeichnis auf dem Datenträger ist identisch mit dem Projekt in der quellcodeverwaltung.|  
|SCC_I_FILESDIFFER|Das Verzeichnis auf dem Datenträger unterscheidet sich von dem Projekt in der quellcodeverwaltung.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
|SCC_E_FILENOTCONTROLLED|Das Verzeichnis ist nicht unter quellcodeverwaltung befindet.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|  
|SCC_E_FILENOTEXIST|Lokales Verzeichnis konnte nicht gefunden werden.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion wird verwendet, um anzuweisen, das Quellcodeverwaltungs-Plug-In für den Benutzer eine Liste der Änderungen an einem angegebenen Verzeichnis anzuzeigen. Das plug-in eigenen Fenster geöffnet, in einem Format seiner Wahl, um die Unterschiede zwischen dem Verzeichnis des Benutzers auf dem Datenträger und das entsprechende Projekt unter Versionskontrolle anzuzeigen.  
  
 Wenn ein Vergleich-Plug-in unterstützt von Verzeichnissen im Vorfeld für alle muss es Vergleich von Verzeichnissen auf Basis von Dateinamen unterstützen, auch wenn die Optionen "Quick-Diff" nicht unterstützt werden.  
  
|`dwFlags`|Interpretation|  
|---------------|--------------------|  
|SCC_DIFF_IGNORECASE|Groß-/Kleinschreibung Vergleich (kann für schnelle Diff oder Visual verwendet werden).|  
|SCC_DIFF_IGNORESPACE|Ignoriert Leerzeichen (kann für schnelle / Diff- oder Visual verwendet werden).|  
|SCC_DIFF_QD_CONTENTS|Wenn durch das Quellcodeverwaltungs-Plug-Ins unterstützt, werden automatisch im Verzeichnis byteweise verglichen.|  
|SCC_DIFF_QD_CHECKSUM|Wenn von-Plug-in unterstützt werden, im Hintergrund des Verzeichnisses über eine Prüfsumme verglichen, wenn nicht unterstützt, auf SCC_DIFF_QD_CONTENTS zurück fällt.|  
|SCC_DIFF_QD_TIME|Wenn von-Plug-in unterstützt werden, im Hintergrund des Verzeichnisses über die Zeitstempel vergleicht oder, wenn nicht unterstützt, auf SCC_DIFF_QD_CHECKSUM oder SCC_DIFF_QD_CONTENTS zurück fällt.|  
  
> [!NOTE]
>  Diese Funktion verwendet die gleichen Befehlsflags als die [SccDiff](../extensibility/sccdiff-function.md). Ein Quellcodeverwaltungs-Plug-In können jedoch die "Quick-Diff"-Vorgang für Verzeichnisse wird nicht unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)