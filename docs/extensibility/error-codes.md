---
title: "Fehlercodes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fehlercodes, Source Control-Plug-ins"
  - "Source Control-Plug-ins Fehlercodes"
  - "Fehler [Visual Studio SDK]"
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Fehlercodes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn eine Source Control\-Plug\-in API\-Funktion einen Fehler zurückgibt, wird davon ausgegangen, einer der folgenden Fehlercodes werden. Alle Fehler werden Warnungen oder nur zu Informationszwecken Fehlercodes sind positiv, negativ und Erfolg ist 0.  
  
|Fehlercode|Wert|Beschreibung|  
|----------------|----------|------------------|  
|`SCC_I_SHARESUBPROJOK`|7|\-Plug\-in unterstützt das Hinzufügen von Dateien aus der quellcodeverwaltung in zwei Schritten. Weitere Informationen finden Sie unter [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Die lokale Datei unterscheidet sich von der Datei im Quellcode\-Verwaltungsdatenbank \(z. B. [SccDiff](../extensibility/sccdiff-function.md) kann dieser Wert zurückgeben\).|  
|`SCC_I_RELOADFILE`|5|Lokaler Datei wurde während des Vorgangs der Datenquellen\-Steuerelement geändert. die IDE Neuladen der Datei sollten wenn möglich.|  
|`SCC_I_FILENOTAFFECTED`|4|Die Datei ist nicht betroffen.|  
|`SCC_I_PROJECTCREATED`|3|Das Projekt wurde während des Vorgangs der Datenquellen\-Steuerelement erstellt \(z. B. während eines Aufrufs [SccOpenProject](../extensibility/sccopenproject-function.md) beim `SCC_OP_CREATEIFNEW` \-Flag angegeben ist\).|  
|`SCC_I_OPERATIONCANCELED`|2|Vorgang wurde abgebrochen.|  
|`SCC_I_ADV_SUPPORT`|1|Plug\-in unterstützt erweiterte Optionen für den angegebenen Befehl. Weitere Informationen finden Sie unter [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Erfolgreich.|  
|`SCC_E_INITIALIZEFAILED`|\-1|Fehler: Fehler bei der Initialisierung.|  
|`SCC_E_UNKNOWNPROJECT`|\-2|Fehler: Projekt ist unbekannt.|  
|`SCC_E_COULDNOTCREATEPROJECT`|\-3|Fehler: das Projekt konnte nicht erstellt werden.|  
|`SCC_E_NOTCHECKEDOUT`|\-4|Fehler: die Datei ist nicht ausgecheckt.|  
|`SCC_E_ALREADYCHECKEDOUT`|\-5|Fehler: die Datei ist bereits ausgecheckt.|  
|`SCC_E_FILEISLOCKED`|\-6|Fehler: die Datei ist gesperrt.|  
|`SCC_E_FILEOUTEXCLUSIVE`|\-7|Fehler: die Datei ist exklusiv ausgecheckt.|  
|`SCC_E_ACCESSFAILURE`|\-8|Es wurde ein Problem, das Zugriff auf Quellcode\-Verwaltungssystem, möglicherweise aufgrund eines Netzwerk\-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|`SCC_E_CHECKINCONFLICT`|\-9|Fehler: Es wurde ein Konflikt beim Einchecken.|  
|`SCC_E_FILEALREADYEXISTS`|\-10|Fehler: die Datei ist bereits vorhanden.|  
|`SCC_E_FILENOTCONTROLLED`|\-11|Fehler: die Datei ist nicht in einem Quellcodeverwaltungsprojekt.|  
|`SCC_E_FILEISCHECKEDOUT`|\-12|Fehler: die Datei ausgecheckt ist.|  
|`SCC_E_NOSPECIFIEDVERSION`|\-13|Fehler: Es ist keine Version angegeben.|  
|`SCC_E_OPNOTSUPPORTED`|\-14|Fehler: der Vorgang wird nicht unterstützt.|  
|`SCC_E_NONSPECIFICERROR`|\-15|Nicht angegebenen Fehler.|  
|`SCC_E_OPNOTPERFORMED`|\-16|Fehler: der Vorgang wurde nicht ausgeführt.|  
|`SCC_E_TYPENOTSUPPORTED`|\-17|Fehler: der Typ der Datei, z. B. binär, wird durch das Quellcodeverwaltungssystem nicht unterstützt.|  
|`SCC_E_VERIFYMERGE`|\-18|Datei automatisch zusammengeführt wurde, aber nicht, da es ist eine benutzerüberprüfung der ausstehenden eingecheckt wurde.|  
|`SCC_E_FIXMERGE`|\-19|Datei automatisch zusammengeführt wurde, aber nicht in eingecheckt wurde aufgrund eines Konflikts von zusammenführen, das manuell behoben werden müssen.|  
|`SCC_E_SHELLFAILURE`|\-20|Fehler aufgrund eines Fehlers Shell.|  
|`SCC_E_INVALIDUSER`|\-21|Fehler: der Benutzer ist ungültig.|  
|`SCC_E_PROJECTALREADYOPEN`|\-22|Fehler: das Projekt ist bereits geöffnet.|  
|`SCC_E_PROJSYNTAXERR`|\-23|Projekt\-Syntaxfehler.|  
|`SCC_E_INVALIDFILEPATH`|\-24|Fehler: der Pfad ist ungültig.|  
|`SCC_E_PROJNOTOPEN`|\-25|Fehler: das Projekt ist nicht geöffnet.|  
|`SCC_E_NOTAUTHORIZED`|\-26|Fehler: der Benutzer ist nicht zum Ausführen dieses Vorgangs autorisiert.|  
|`SCC_E_FILESYNTAXERR`|\-27|Datei\-Syntaxfehler.|  
|`SCC_E_FILENOTEXIST`|\-28|Fehler, die lokale Datei existiert nicht.|  
|`SCC_E_CONNECTIONFAILURE`|\-29|Fehler: Fehler bei Verbindung.|  
|`SCC_E_UNKNOWNERROR`|\-30|Ein Fehler aufgetreten.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|\-31|Hintergrund\-Get\-Vorgang wird aktuell ausgeführt.|  
  
## Für die schnelle Überprüfung bereitgestellten Makros  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE) IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE) IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## Hinweise  
 Alle Source Control\-Plug\-in API\-Funktionen \(mit Ausnahme der [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), und [SccDiff](../extensibility/sccdiff-function.md)\) sollten erfolgreich sein, wenn die lokalen Dateien, die als Argumente übergeben werden, nicht im Arbeitsordner vorhanden sind. Die IDE kann z. B. einen Aufruf von Ausstellen der [SccCheckout](../extensibility/scccheckout-function.md) oder [SccUncheckout](../extensibility/sccuncheckout-function.md) auf eine Datei, die in dem Ordner nicht vorhanden, aber im Quellcode\-Verwaltungssystem vorhanden ist. Dieser Aufruf erfolgreich ausgeführt werden kann. Nur, wenn keine Datei im Arbeitsverzeichnis oder in das Quellcodeverwaltungssystem wird die Funktion ein Fehler erwartet.  
  
 Bestimmte Funktionen, wie z. B. `SccAdd` und `SccCheckin`, sollte insbesondere zurückgeben `SCC_E_FILENOTEXIST` Wenn die Datei im Arbeitsordner ist nicht vorhanden. Andere Funktionen sind erfolgreich, wenn die Arbeitsdatei nicht vorhanden ist, wenn die Funktionen auf einen gültigen Dateinamen im Quellcode\-Verwaltungssystem angewendet werden soll.  
  
 Das Quellcodeverwaltungs\-Plug\-in sollten keine Annahmen bezüglich der Berechtigungen auf eine Datei in den Arbeitsordner, selbst wenn der Plug\-in\-Datei bei einigen Vorgängen während schreibgeschützt war. Eine Datei im Arbeitsordner kann verschoben, gelöscht und außerhalb des Plug\-ins des Steuerelements geändert werden.  
  
## Siehe auch  
 [Source Control\-Plug\-ins](../extensibility/source-control-plug-ins.md)