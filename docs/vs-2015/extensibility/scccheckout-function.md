---
title: Scccheckout-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f23290ebfadd1b6e3d34f808d5ea0ccccbb3c319
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200153"
---
# <a name="scccheckout-function"></a>SccCheckout-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine Liste der voll qualifizierten Dateinamen angegeben wird, werden Sie von dieser Funktion auf das lokale Laufwerk überprüft. Der Kommentar gilt für alle Dateien, die ausgecheckt werden. Das Kommentar Argument kann eine `null` Zeichenfolge sein.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 pvcontext  
 in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.  
  
 hWnd  
 in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.  
  
 nnoch  
 in Anzahl der Dateien, die für das Auschecken ausgewählt wurden.  
  
 lpfile-Namen  
 in Array von voll qualifizierten lokalen Pfadnamen von Dateien, die ausgecheckt werden sollen.  
  
 lpcomment  
 in Der Kommentar, der auf jede der ausgewählten Dateien angewendet werden soll, die ausgecheckt werden.  
  
 f-Optionen  
 in Befehlsflags (siehe [Bitflags, die von bestimmten Befehlen verwendet werden](../extensibility/bitflags-used-by-specific-commands.md)).  
  
 pvoptions  
 in Plug-in-spezifische Optionen für die Quell Code Verwaltung.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Das Auschecken war erfolgreich.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei befindet sich nicht unter Quell Code Verwaltung.|  
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler. Die Datei wurde nicht ausgecheckt.|  
|SCC_E_ALREADYCHECKEDOUT|Der Benutzer hat die Datei bereits ausgecheckt.|  
|SCC_E_FILEISLOCKED|Die Datei ist gesperrt, und das Erstellen neuer Versionen wird untersagt.|  
|SCC_E_FILEOUTEXCLUSIVE|Ein anderer Benutzer hat einen exklusiven Auscheck Vorgang für diese Datei durchgeführt.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen der Quellcodeverwaltungs-Plug-in](../extensibility/source-control-plug-in-api-functions.md)   
 [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)
