---
title: SccAdd Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 2933d00b7450f946a5fd5409bcaeecc2527a9f64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139545"
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
  
#### <a name="parameters"></a>Parameter  
 pvContext  
 [in] Datenquellen-Steuerelement-Plug-in-Context-Struktur.  
  
 hWnd  
 [in] Ein Handle für die IDE-Fenster, das das Quellsteuerelement-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die es bereitstellt.  
  
 nFiles  
 [in] Anzahl der Dateien ausgewählt, die für das aktuelle Projekt in festgelegten hinzugefügt werden die `lpFileNames` Array.  
  
 lpFileNames  
 [in] Array von vollständig qualifizierten lokalen Namen der zu hinzuzufügenden Dateien.  
  
 lpComment  
 [in] Der Kommentar auf alle hinzugefügten Dateien angewendet werden soll.  
  
 pfOptions  
 [in] Array von Befehlsflags, bereitgestellt auf einer pro Datei vorgehen.  
  
 pvOptions  
 [in] Quellcodeverwaltungs-plug-in spezifischen Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Source Control-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|SCC_OK|Die Add-Vorgang war erfolgreich.|  
|SCC_E_FILEALREADYEXISTS|Die ausgewählte Datei ist bereits in der quellcodeverwaltung.|  
|SCC_E_TYPENOTSUPPORTED|Der Typ der Datei (z. B. binäre) wird durch das Quellcodeverwaltungssystem nicht unterstützt.|  
|SCC_E_OPNOTSUPPORTED|Dieser Vorgang wird von das Quellcodeverwaltungssystem nicht unterstützt.|  
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Fügen Sie nicht ausgeführt.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
|SCC_E_FILENOTEXIST|Lokale Datei wurde nicht gefunden.|  
  
## <a name="remarks"></a>Hinweise  
 Die üblichen `fOptions` werden durch ein Array hier ersetzt `pfOptions`, mit einem `LONG` option Spezifikation pro Datei. Dies liegt daran der Dateityp aus Datei variieren kann.  
  
> [!NOTE]
>  Es ist nicht zulässig, beide anzugeben `SCC_FILETYPE_TEXT` und `SCC_FILETYPE_BINARY` Optionen für die gleiche Datei, aber es ist zulässig, die keines von beiden angeben. Keine Einstellung entspricht der Einstellung `SCC_FILETYPE_AUTO`, in diesem Fall die Quelle-Plug-in erkennt automatisch den Dateityp zu steuern.  
  
 Im folgenden finden Sie die Liste der Flags, die der `pfOptions` Array:  
  
|Option|Wert|Bedeutung|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0 x 00|Die Datenquellen-Steuerelement-Plug-in sollte den Dateityp erkennen.|  
|SCC_FILETYPE_TEXT|0 x 01|Gibt eine ASCII-Textdatei an.|  
|SCC_FILETYPE_BINARY|0 x 02|Gibt einen Dateityp als ASCII-Text an.|  
|SCC_ADD_STORELATEST|0x04|Speichert nur die letzte Kopie der Datei, die keine Deltas an.|  
|SCC_FILETYPE_TEXT_ANSI|0 x 08|Die Datei behandelt als ANSI-Text.|  
|SCC_FILETYPE_UTF8|0x10|Behandelt die Datei als Unicode-Text im UTF8-Format an.|  
|SCC_FILETYPE_UTF16LE|0x20|Behandelt die Datei als Unicode-Text im UTF16-Little-Endian-Format.|  
|SCC_FILETYPE_UTF16BE|0 x 40|Behandelt die Datei als UTF16-Format Big-Endian Unicode-Text formatieren.|  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)