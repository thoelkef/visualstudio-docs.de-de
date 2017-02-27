---
title: "SccCheckin-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCheckin"
helpviewer_keywords: 
  - "SccCheckin-Funktion"
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# SccCheckin-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion prüft in zuvor ausgecheckten Dateien in das Quellcodeverwaltungssystem Änderungen gespeichert, und erstellen eine neue Version. Diese Funktion ist mit einem Zähler und ein Array der Namen der Dateien, die eingecheckt werden aufgerufen.  
  
## Syntax  
  
```cpp#  
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
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das die SCC\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 \[in\] Anzahl der Dateien, die eingecheckt werden ausgewählt.  
  
 lpFileNames  
 \[in\] Array von Namen voll gekennzeichneter lokaler Pfad Dateien eingecheckt werden.  
  
 lpComment  
 \[in\] Kommentar auf der ausgewählten eingecheckten Dateien angewendet werden. Dies ist `NULL` wenn das Quellcodeverwaltungs\-Plug\-In für einen Kommentar auffordern soll.  
  
 Bestanden  
 \[in\] Befehl Flags, die entweder 0 oder `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 \[in\] SCC\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Dateien erfolgreich eingecheckt wurde.|  
|SCC\_E\_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht vom Quellcode gesteuert.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler. Datei wurde nicht eingecheckt.|  
|SCC\_E\_NOTCHECKEDOUT|Der Benutzer hat die Datei, sodass sie nicht Einchecken nicht ausgecheckt.|  
|SCC\_E\_CHECKINCONFLICT|Einchecken konnte nicht durchgeführt werden:<br /><br /> -   Ein anderer Benutzer hat nun eingecheckt und `bAutoReconcile` war falsch.<br /><br /> \- oder \-<br /><br /> -   \(Beispielsweise, wenn Dateien binär sind\), kann die automatische Zusammenführung ausgeführt werden.|  
|SCC\_E\_VERIFYMERGE|Datei automatisch zusammengeführt wurde, aber nicht eingecheckt wurde ausstehende Überprüfung des Benutzers.|  
|SCC\_E\_FIXMERGE|Datei automatisch zusammengeführt wurde, aber nicht in eingecheckt wurde aufgrund eines Konflikts von zusammenführen, das manuell behoben werden müssen.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_I\_OPERATIONCANCELED|Vorgang wurde vor dem Abschluss abgebrochen.|  
|SCC\_I\_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
|SCC\_E\_FILENOTEXIST|Lokaler Datei wurde nicht gefunden.|  
  
## Hinweise  
 Der Kommentar gilt für alle eingecheckten Dateien. Das Kommentar\-Argument kann eine `null` Zeichenfolge, die in diesem Fall kann das Quellcodeverwaltungs\-Plug\-in einen Kommentar für die einzelnen Dateien abgefragt.  
  
 Die `fOptions` Argument kann einen Wert erhält das `SCC_KEEP_CHECKEDOUT` Flag an, dass die Absicht des Benutzers, die Datei einzuchecken, und probieren Sie es erneut.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)