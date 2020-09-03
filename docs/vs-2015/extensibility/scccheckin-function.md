---
title: Scccheckin-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8a5a91a0300f256b66970403a3431edf0fe757e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189528"
---
# <a name="scccheckin-function"></a>SccCheckin-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion überprüft zuvor ausgecheckte Dateien an das Quell Code Verwaltungssystem, speichert die Änderungen und erstellt eine neue Version. Diese Funktion wird mit einer Anzahl und einem Array von Namen der zu überprüfenden Dateien aufgerufen.  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 pvcontext  
 in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.  
  
 hWnd  
 in Ein Handle für das IDE-Fenster, das von dem SCC-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.  
  
 nnoch  
 in Anzahl der Dateien, die für das Einchecken ausgewählt wurden.  
  
 lpfile-Namen  
 in Array von voll qualifizierten lokalen Pfadnamen von Dateien, die eingesucht werden sollen.  
  
 lpcomment  
 in Der Kommentar, der auf jede der ausgewählten Dateien angewendet werden soll, die eingeklickt werden. Dies ist `NULL` der Wert, wenn das Quellcodeverwaltungs-Plug-in zur Eingabe eines Kommentars auffordern soll.  
  
 f-Optionen  
 in Befehlsflags, entweder 0 oder `SCC_KEEP_CHECKEDOUT` .  
  
 pvoptions  
 in SCC-Plug-in-spezifische Optionen.  
  
## <a name="return-value"></a>Rückgabewert  
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SCC_OK|Die Dateien wurden erfolgreich eingeglichen.|  
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei befindet sich nicht unter Quell Code Verwaltung.|  
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|  
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler. Die Datei wurde nicht eingeglichen.|  
|SCC_E_NOTCHECKEDOUT|Der Benutzer hat die Datei nicht ausgecheckt und kann Sie daher nicht einchecken.|  
|SCC_E_CHECKINCONFLICT|Eincheck Vorgang konnte aufgrund von folgenden Aktionen nicht ausgeführt werden:<br /><br /> -Ein anderer Benutzer hat sich im Voraus eingeglichen und `bAutoReconcile` war false.<br /><br /> - oder -<br /><br /> -Die automatische Zusammenführung kann nicht ausgeführt werden (z. b. wenn Dateien Binär sind).|  
|SCC_E_VERIFYMERGE|Die Datei wurde automatisch zusammengeführt, aber die ausstehende Benutzer Überprüfung wurde nicht geprüft.|  
|SCC_E_FIXMERGE|Die Datei wurde automatisch zusammengeführt, aber aufgrund eines Mergekonflikts, der manuell aufgelöst werden muss, nicht eingeglichen.|  
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|  
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor dem Abschluss abgebrochen.|  
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss erneut geladen werden.|  
|SCC_E_FILENOTEXIST|Die lokale Datei wurde nicht gefunden.|  
  
## <a name="remarks"></a>Bemerkungen  
 Der Kommentar gilt für alle Dateien, die eingeklickt werden. Das Kommentar Argument kann eine `null` Zeichenfolge sein. in diesem Fall kann das Quellcodeverwaltungs-Plug-in den Benutzer zur Eingabe einer Kommentar Zeichenfolge für jede Datei auffordern.  
  
 Dem `fOptions` -Argument kann ein Wert des `SCC_KEEP_CHECKEDOUT` -Flags zugewiesen werden, um anzugeben, dass die Absicht des Benutzers darin besteht, die Datei zu überprüfen und erneut auszuchecken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
