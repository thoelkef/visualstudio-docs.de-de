---
title: SccAdd-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fc2b74b32c0fb90a578644df0065e24eb8e373f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830903"
---
# <a name="sccadd-function"></a>SccAdd-Funktion
Diese Funktion wird vom Quellcodeverwaltungssystem neue Dateien hinzugefügt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
  
### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.  
  
 nFiles  
 [in] Anzahl der Dateien, die wie in dem aktuellen Projekt hinzugefügt werden sollen die `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array von vollständig qualifizierten lokalen Namen der Dateien hinzugefügt werden.  
  
 lpComment  
 [in] Der Kommentar, der auf alle hinzugefügten Dateien angewendet werden.  
  
 pfOptions  
 [in] Array von Befehlsflags auf einer Basis pro Datei bereitgestellt.  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Der Add-Vorgang war erfolgreich.|  
|SCC_E_FILEALREADYEXISTS|Die ausgewählte Datei ist bereits unter quellcodeverwaltung.|  
|SCC_E_TYPENOTSUPPORTED|Der Typ der Datei (z. B. binäre) wird vom Quellcode-Verwaltungssystem nicht unterstützt.|  
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem wird dieser Vorgang nicht unterstützt.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Fügen Sie nicht ausgeführt.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|  
|SCC_E_FILENOTEXIST|Lokale Datei wurde nicht gefunden.|  
  
## <a name="remarks"></a>Hinweise  
 Die üblichen `fOptions` werden durch ein Array, hier ersetzt `pfOptions`, mit einem `LONG` option Spezifikation pro Datei. Das liegt der Dateityp von Dateien variieren.  
  
> [!NOTE]
>  Es ist ungültig. Geben Sie beide `SCC_FILETYPE_TEXT` und `SCC_FILETYPE_BINARY` Optionen für die gleiche Datei, aber keines von beiden angegeben ist. Keine Einstellung entspricht der Einstellung `SCC_FILETYPE_AUTO`, in diesem Fall die Quelle-Plug-in erkennt automatisch den Dateityp zu steuern.  
  
 Im folgenden finden Sie die Liste der Flags, die der `pfOptions` Array:  
  
|Option|Wert|Bedeutung|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0 x 00|Das Quellcodeverwaltungs-Plug-in sollte es sich um den Dateityp erkennen.|  
|SCC_FILETYPE_TEXT|0 x 01|Gibt eine ASCII-Textdatei an.|  
|SCC_FILETYPE_BINARY|0 x 02|Gibt einen Dateityp als ASCII-Text an.|  
|SCC_ADD_STORELATEST|0x04|Speichert nur die letzte Kopie der Datei keine Deltas.|  
|SCC_FILETYPE_TEXT_ANSI|0 x 08|Die Datei behandelt als ANSI-Text.|  
|SCC_FILETYPE_UTF8|0x10|Behandelt die Datei als Unicode-Text im UTF8-Format.|  
|SCC_FILETYPE_UTF16LE|0x20|Behandelt die Datei als Unicode-Text im UTF16-Little-Endian-Format.|  
|SCC_FILETYPE_UTF16BE|0 x 40|Behandelt die Datei im UTF16-Format Big-Endian Unicode-Text formatieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)