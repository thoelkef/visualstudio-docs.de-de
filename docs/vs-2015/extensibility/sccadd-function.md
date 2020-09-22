---
title: Sccadd-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: daac15bbb7829d510db17ba02057a2dc86c55990
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840933"
---
# <a name="sccadd-function"></a>SccAdd-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion fügt dem Quell Code Verwaltungssystem neue Dateien hinzu.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 pvcontext  
 in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.  
  
 hWnd  
 in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.  
  
 nnoch  
 in Anzahl der ausgewählten Dateien, die dem aktuellen Projekt hinzugefügt werden sollen, wie im `lpFileNames` Array angegeben.  
  
 lpfile-Namen  
 in Array von voll qualifizierten lokalen Namen von Dateien, die hinzugefügt werden sollen.  
  
 lpcomment  
 in Der Kommentar, der auf alle Dateien angewendet werden soll, die hinzugefügt werden.  
  
 pfoptions  
 in Ein Array von Befehlsflags, die auf Datei Basis bereitgestellt werden.  
  
 pvoptions  
 in Plug-in-spezifische Optionen für die Quell Code Verwaltung.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Der Vorgang zum Hinzufügen war erfolgreich.|  
|SCC_E_FILEALREADYEXISTS|Die ausgewählte Datei befindet sich bereits in der Quell Code Verwaltung.|  
|SCC_E_TYPENOTSUPPORTED|Der Dateityp (z. b. Binary) wird vom Quell Code Verwaltungssystem nicht unterstützt.|  
|SCC_E_OPNOTSUPPORTED|Das Quell Code Verwaltungssystem unterstützt diesen Vorgang nicht.|  
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler. Hinzufügen wurde nicht ausgeführt.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
|SCC_E_FILENOTEXIST|Die lokale Datei wurde nicht gefunden.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die üblichen `fOptions` werden hier durch ein Array ersetzt, `pfOptions` , durch eine `LONG` options Angabe pro Datei. Dies liegt daran, dass der Dateityp von Datei zu Datei variieren kann.  
  
> [!NOTE]
> Es ist ungültig, sowohl `SCC_FILETYPE_TEXT` die- `SCC_FILETYPE_BINARY` Option als auch die-Option für dieselbe Datei anzugeben, aber es ist zulässig, keines der beiden Optionen anzugeben. Die Einstellung keines ist identisch mit der Einstellung `SCC_FILETYPE_AUTO` . in diesem Fall erkennt das Quellcodeverwaltungs-Plug-in automatisch den Dateityp.  
  
 Im folgenden finden Sie eine Liste der im Array verwendeten Flags `pfOptions` :  
  
|Option|Wert|Bedeutung|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|Das Quellcodeverwaltungs-Plug-in sollte den Dateityp erkennen.|  
|SCC_FILETYPE_TEXT|0x01|Gibt eine ASCII-Textdatei an.|  
|SCC_FILETYPE_BINARY|0x02|Gibt einen anderen Dateityp als ASCII-Text an.|  
|SCC_ADD_STORELATEST|0x04|Speichert nur die aktuelle Kopie der Datei, keine Delta.|  
|SCC_FILETYPE_TEXT_ANSI|0x08|Behandelt die Datei als ANSI-Text.|  
|SCC_FILETYPE_UTF8|0x10|Behandelt die Datei als Unicode-Text im UTF8-Format.|  
|SCC_FILETYPE_UTF16LE|0x20|Behandelt die Datei als Unicode-Text im UTF16 Little Endian-Format.|  
|SCC_FILETYPE_UTF16BE|0x40|Behandelt die Datei als Unicode-Text im UTF16 Big Endian-Format.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
