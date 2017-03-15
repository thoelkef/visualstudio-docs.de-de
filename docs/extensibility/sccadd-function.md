---
title: "SccAdd-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccAdd"
helpviewer_keywords: 
  - "SccAdd-Funktion"
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# SccAdd-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion wird vom Quellcodeverwaltungssystem neue Dateien hinzugefügt.  
  
## Syntax  
  
```cpp#  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parameter  
 pvContext  
 \[in\] Source Control\-Plug\-in Context\-Struktur.  
  
 hWnd  
 \[in\] Ein Handle für die IDE\-Fenster, das Quellcodeverwaltungs\-Plug\-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 \[in\] Anzahl der Dateien, die gemäß dem aktuellen Projekt hinzugefügt werden die `lpFileNames` Array.  
  
 lpFileNames  
 \[in\] Array von vollständig qualifizierten lokalen Namen der Dateien hinzugefügt werden.  
  
 lpComment  
 \[in\] Der Kommentar, der auf alle hinzugefügten Dateien angewendet werden.  
  
 pfOptions  
 \[in\] Array von Befehlsflags, pro Datei angegeben.  
  
 pvOptions  
 \[in\] Quellcodeverwaltungs\-plug\-in spezifischen Optionen.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Die Add\-Vorgang war erfolgreich.|  
|SCC\_E\_FILEALREADYEXISTS|Die ausgewählte Datei ist bereits in einem Quellcodeverwaltungsprojekt.|  
|SCC\_E\_TYPENOTSUPPORTED|Der Typ der Datei \(z. B. binäre\) wird vom Quellcode\-Verwaltungssystem nicht unterstützt.|  
|SCC\_E\_OPNOTSUPPORTED|Dieser Vorgang wird von Quellcode\-Verwaltungssystem nicht unterstützt.|  
|SCC\_E\_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC\_E\_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC\_E\_NONSPECIFICERROR|Unspezifischen Ausfall. Fügen Sie nicht ausgeführt.|  
|SCC\_I\_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
|SCC\_I\_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
|SCC\_E\_FILENOTEXIST|Lokaler Datei wurde nicht gefunden.|  
  
## Hinweise  
 Die üblichen `fOptions` werden hier ersetzt durch ein Array `pfOptions`, mit einem `LONG` option Spezifikation pro Datei. Dies ist, da der Dateityp in der die Dateien variieren kann.  
  
> [!NOTE]
>  Es ist unzulässig, beide geben `SCC_FILETYPE_TEXT` und `SCC_FILETYPE_BINARY` Optionen für die gleiche Datei, aber es ist keines von beiden angeben. Keine Einstellung entspricht der Einstellung `SCC_FILETYPE_AUTO`, in diesem Fall die Quellcode\-Plug\-in erkennt automatisch den Dateityp.  
  
 Im folgenden finden Sie die Liste der Flags, die der `pfOptions` Array:  
  
|Option|Wert|Bedeutung|  
|------------|----------|---------------|  
|SCC\_FILETYPE\_AUTO|0 x 00|Den Dateityp sollte das Quellcodeverwaltungs\-Plug\-in erkannt werden.|  
|SCC\_FILETYPE\_TEXT|0 x 01|Gibt eine ASCII\-Textdatei an.|  
|SCC\_FILETYPE\_BINARY|0 x 02|Gibt einen Dateityp als ASCII\-Text an.|  
|SCC\_ADD\_STORELATEST|0 x 04|Speichert nur die letzte Kopie der Datei keine Deltas.|  
|SCC\_FILETYPE\_TEXT\_ANSI|0 x 08|Wird die Datei als ANSI\-Text behandelt.|  
|SCC\_FILETYPE\_UTF8|0 x 10|Behandelt die Datei als Unicode\-Text im UTF8\-Format.|  
|SCC\_FILETYPE\_UTF16LE|0 x 20|Behandelt die Datei als Unicode\-Text im UTF16\-Little\-Endian\-Format.|  
|SCC\_FILETYPE\_UTF16BE|0 x 40|Behandelt die Datei als Unicode\-Text in UTF16 Big Endian formatieren.|  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)