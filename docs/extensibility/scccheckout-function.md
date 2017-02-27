---
title: "SccCheckout-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCheckout"
helpviewer_keywords: 
  - "SccCheckout-Funktion"
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCheckout-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn eine Liste der vollqualifizierten Dateinamen, checkt diese Funktion sie auf dem lokalen Laufwerk. Der Kommentar gilt für alle Dateien, die ausgecheckt wird. Das Kommentar\-Argument kann eine `null` Zeichenfolge.  
  
## Syntax  
  
```cpp#  
SCCRTN SccCheckout (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 \[in\] Anzahl der Dateien, die ausgecheckt werden ausgewählt.  
  
 lpFileNames  
 \[in\] Array von Namen voll gekennzeichneter lokaler Pfad Dateien ausgecheckt werden.  
  
 lpComment  
 \[in\] Kommentar auf der ausgewählten Dateien ausgecheckt wird, angewendet werden.  
  
 Bestanden  
 \[in\] Befehl Flags \(siehe [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md)\).  
  
 pvOptions  
 \[in\] Quellcodeverwaltungs\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Auschecken war erfolgreich.|  
|SCC\_E\_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht vom Quellcode gesteuert.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_NONSPECIFICERROR|Nicht spezifischen Fehler. Die Datei wurde nicht ausgecheckt.|  
|SCC\_E\_ALREADYCHECKEDOUT|Der Benutzer hat bereits die Datei ausgecheckt haben.|  
|SCC\_E\_FILEISLOCKED|Die Datei ist gesperrt, verhindern die Erstellung neuer Versionen.|  
|SCC\_E\_FILEOUTEXCLUSIVE|Ein anderer Benutzer hat ein exklusives Auschecken für diese Datei ausgeführt.|  
|SCC\_I\_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [Bitflags, die von bestimmten Befehlen verwendet](../extensibility/bitflags-used-by-specific-commands.md)