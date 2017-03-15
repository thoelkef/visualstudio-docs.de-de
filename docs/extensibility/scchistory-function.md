---
title: "SccHistory-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccHistory"
helpviewer_keywords: 
  - "SccHistory-Funktion"
ms.assetid: a636d9d3-47c1-4b48-ac6b-bcfde19d6cf9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccHistory-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion zeigt den Verlauf der angegebenen Dateien.  
  
## Syntax  
  
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
  
#### Parameter  
 `pvContext`  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 `hWnd`  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 `nFiles`  
 \[in\] Anzahl der angegebenen Dateien in den `lpFileName` Array.  
  
 `lpFileName`  
 \[in\] Array von vollständig qualifizierten Namen von Dateien.  
  
 `fOptions`  
 \[in\] Befehl Flags \(zurzeit nicht verwendet\).  
  
 `pvOptions`  
 \[in\] Quellcodeverwaltungs\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Versionsverlauf wurde erfolgreich abgerufen.|  
|SCC\_I\_RELOADFILE|Quellcode\-Verwaltungssystem Änderung der Datei auf dem Datenträger tatsächlich beim Abrufen des Verlaufs \(z. B. durch Abrufen einer alten Version davon\), damit die IDE diese Datei neu geladen werden soll.|  
|SCC\_E\_FILENOTCONTROLLED|Diese Datei befindet sich nicht in Datenquellen\-Steuerelement.|  
|SCC\_E\_OPNOTSUPPORTED|Dieser Vorgang wird von Quellcode\-Verwaltungssystem nicht unterstützt.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_PROJNOTOPEN|Das Projekt wurde nicht geöffnet.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler. Dateiversionsverlauf konnte nicht abgerufen werden.|  
  
## Hinweise  
 Das Quellcodeverwaltungs\-Plug\-in kann ein eigenes Dialogfeld, um den Verlauf jeder Datei anzeigen Anzeigen mit `hWnd` als übergeordnetes Fenster. Alternativ können Sie der optionale Text Rückruf Ausgabe Funktion angegeben wird, um die [SccOpenProject](../extensibility/sccopenproject-function.md) kann verwendet werden, wenn es unterstützt wird.  
  
 Beachten Sie, dass unter bestimmten Umständen ist die Datei, die überprüft wird während der Ausführung dieses Aufrufs ändern kann. Zum Beispiel die [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] History\-Befehl hat dem Benutzer die Möglichkeit, eine alte Version der Datei abrufen. In diesem Fall die Quellcode\-Plug\-Ins gibt `SCC_I_RELOAD` um der IDE zu warnen, dass die Datei neu geladen werden muss.  
  
> [!NOTE]
>  Wenn das Quellcodeverwaltungs\-Plug\-In für ein Array von Dateien diese Funktion unterstützt, kann nur der Dateiversionsgeschichte für die erste Datei angezeigt werden.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)