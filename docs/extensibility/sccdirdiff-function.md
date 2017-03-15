---
title: "SccDirDiff-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccDirDiff"
helpviewer_keywords: 
  - "SccDirDiff-Funktion"
ms.assetid: 26c9ba92-e3b9-4dd2-bd5e-76b17745e308
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccDirDiff-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion zeigt die Unterschiede zwischen der aktuellen lokalen Verzeichnis auf dem Client\-Datenträger und das entsprechende Projekt unter Versionskontrolle.  
  
## Syntax  
  
```cpp#  
SCCRTN SccDirDiff(  
   LPVOID    pContext,  
   HWND      hWnd,  
   LPCSTR    lpDirName,  
   LONG      dwFlags,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parameter  
 "pContext"  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 lpDirName  
 \[in\] Voll gekennzeichnete Pfad in das lokale Verzeichnis für das Anzeigen eines visuellen Unterschied.  
  
 dwFlags  
 \[in\] Befehl Flags \(siehe Hinweise Abschnitt\).  
  
 pvOptions  
 \[in\] Quellcodeverwaltungs\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Das Verzeichnis auf dem Datenträger ist identisch mit dem Projekt im Quellcode.|  
|SCC\_I\_FILESDIFFER|Das Verzeichnis auf dem Datenträger unterscheidet sich von dem Projekt im Quellcode.|  
|SCC\_I\_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
|SCC\_E\_FILENOTCONTROLLED|Das Verzeichnis ist nicht vom Quellcode gesteuert.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Nicht spezifischen Fehler.|  
|SCC\_E\_FILENOTEXIST|Lokales Verzeichnis konnte nicht gefunden werden.|  
  
## Hinweise  
 Diese Funktion wird verwendet, um anzuweisen, das Quellcodeverwaltungs\-Plug\-In für den Benutzer eine Liste der Änderungen in einem angegebenen Verzeichnis anzuzeigen. Das plug\-in wird in einem Format seiner Wahl, zum Anzeigen der Unterschiede zwischen Verzeichnis auf der Festplatte des Benutzers und das entsprechende Projekt unter Versionskontrolle ein eigenen Fenster geöffnet.  
  
 Wenn einen Vergleich\-Plug\-in unterstützt alle Verzeichnisse, muss es Vergleich von Verzeichnissen auf Basis von Dateinamen unterstützen, auch wenn die Optionen "Quick\-Diff" nicht unterstützt werden.  
  
|`dwFlags`|Interpretation|  
|---------------|--------------------|  
|SCC\_DIFF\_IGNORECASE|Zwischen Groß\-und Kleinschreibung \(kann für schnelle Diff oder visuellen verwendet werden\).|  
|SCC\_DIFF\_IGNORESPACE|Ignoriert Leerzeichen \(kann für die schnelle Diff oder Visual verwendet werden\).|  
|SCC\_DIFF\_QD\_CONTENTS|Wenn das Quellcodeverwaltungs\-Plug\-in unterstützt, werden im Hintergrund im Verzeichnis byteweise verglichen.|  
|SCC\_DIFF\_QD\_CHECKSUM|Wenn vom plug\-in unterstützt, im Hintergrund das Verzeichnis über eine Prüfsumme verglichen oder, wird nicht unterstützt, auf SCC\_DIFF\_QD\_CONTENTS ausgewichen.|  
|SCC\_DIFF\_QD\_TIME|Wenn vom plug\-in unterstützt, im Hintergrund das Verzeichnis über die Zeitstempel vergleicht oder, wird nicht unterstützt, auf SCC\_DIFF\_QD\_CHECKSUM oder SCC\_DIFF\_QD\_CONTENTS ausgewichen.|  
  
> [!NOTE]
>  Diese Funktion verwendet die gleichen Befehlsflags als die [SccDiff](../extensibility/sccdiff-function.md). Allerdings können ein Quellcodeverwaltungs\-Plug\-In für Verzeichnisse "Quick\-Diff" dieser Vorgang nicht unterstützt.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)