---
title: Fehlercodes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6feb9bfa3b2adb437fd03b5c0b8d4448df4b6f50
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130773"
---
# <a name="error-codes"></a>Fehlercodes
Wenn eine Quelle Steuerelement-Plug-in-API-Funktion einen Fehler zurückgibt, muss es eine der folgenden Fehlercodes werden. Alle Fehler werden Warnungen oder nur zu Informationszwecken Fehlercodes sind positiv, negativ ist, und Erfolg ist 0.  
  
|Fehlercode|Wert|Beschreibung|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|-Plug-in unterstützt das Hinzufügen von Dateien aus der quellcodeverwaltung in zwei Schritten. Weitere Informationen finden Sie unter [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Die lokale Datei unterscheidet sich von der Datei in der Quellcode-Verwaltungsdatenbank (z. B. [SccDiff](../extensibility/sccdiff-function.md) kann dieser Wert zurückgeben).|  
|`SCC_I_RELOADFILE`|5|Lokale Datei wurde während des Vorgangs der Datenquellen-Steuerelement geändert. die IDE soll die Datei nach Möglichkeit neu geladen.|  
|`SCC_I_FILENOTAFFECTED`|4|Die Datei wird nicht beeinflusst.|  
|`SCC_I_PROJECTCREATED`|3|Das Projekt wurde während des Vorgangs der Datenquellen-Steuerelement erstellt (z. B. während eines Aufrufs [SccOpenProject](../extensibility/sccopenproject-function.md) Wenn `SCC_OP_CREATEIFNEW` -Flag angegeben ist).|  
|`SCC_I_OPERATIONCANCELED`|2|Vorgang wurde abgebrochen.|  
|`SCC_I_ADV_SUPPORT`|1|-Plug-in unterstützt erweiterte Optionen für den angegebenen Befehl. Weitere Informationen finden Sie unter [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Erfolgreich.|  
|`SCC_E_INITIALIZEFAILED`|-1|Fehler: Fehler bei der Initialisierung.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Fehler: das Projekt ist unbekannt.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Fehler: das Projekt konnte nicht erstellt werden.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Fehler: die Datei ist nicht ausgecheckt.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Fehler: die Datei ist bereits ausgecheckt.|  
|`SCC_E_FILEISLOCKED`|-6|Fehler: die Datei ist gesperrt.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Fehler: die Datei ist exklusiv ausgecheckt.|  
|`SCC_E_ACCESSFAILURE`|-8|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, wahrscheinlich aufgrund eines Netzwerk-oder Konflikte. Eine Wiederholung wird empfohlen.|  
|`SCC_E_CHECKINCONFLICT`|-9|Fehler: Es wurde ein Konflikt beim Einchecken.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Fehler: die Datei ist bereits vorhanden.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Fehler: die Datei ist nicht in der quellcodeverwaltung.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Fehler: die Datei ausgecheckt wird.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Fehler: Es ist keine Version angegeben.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Fehler: der Vorgang wird nicht unterstützt.|  
|`SCC_E_NONSPECIFICERROR`|-15|Unspezifischer Fehler.|  
|`SCC_E_OPNOTPERFORMED`|-16|Fehler: der Vorgang wurde nicht ausgeführt.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Fehler: der Typ der Datei, z. B. binary, wird von der Quellcodeverwaltungs-System nicht unterstützt.|  
|`SCC_E_VERIFYMERGE`|-18|Datei automatisch zusammengeführt wurde, aber es wurde nicht überprüft wurde, weil es ausstehende benutzerüberprüfung ist.|  
|`SCC_E_FIXMERGE`|-19|Datei automatisch zusammengeführt wurde, jedoch nicht in eingecheckt wurde aufgrund eines Mergekonflikts, das manuell behoben werden muss.|  
|`SCC_E_SHELLFAILURE`|-20|Fehler aufgrund eines Fehlers Shell.|  
|`SCC_E_INVALIDUSER`|-21|Fehler: der Benutzer ist ungültig.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Fehler: das Projekt ist bereits geöffnet.|  
|`SCC_E_PROJSYNTAXERR`|-23|Projekt-Syntaxfehler.|  
|`SCC_E_INVALIDFILEPATH`|-24|Fehler: der Dateipfad ist ungültig.|  
|`SCC_E_PROJNOTOPEN`|-25|Fehler: das Projekt ist nicht geöffnet.|  
|`SCC_E_NOTAUTHORIZED`|-26|Fehler: der Benutzer ist nicht zum Ausführen dieses Vorgangs berechtigt.|  
|`SCC_E_FILESYNTAXERR`|-27|Datei Syntaxfehler.|  
|`SCC_E_FILENOTEXIST`|-28|Fehler, die lokale Datei ist nicht vorhanden.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Fehler: ein Verbindungsfehler aufgetreten.|  
|`SCC_E_UNKNOWNERROR`|-30|Unbekannter Fehler.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Get-Vorgang im Hintergrund wird derzeit ausgeführt.|  
  
## <a name="macros-provided-for-quick-checking"></a>Für die schnelle Überprüfung der bereitgestellten Makros  
  
```cpp  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Hinweise  
 Alle Datenquellen-Steuerelement-Plug-in-API-Funktionen (mit Ausnahme der [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), und [SccDiff](../extensibility/sccdiff-function.md)) voraussichtlich erfolgreich sein, wenn die lokalen Dateien, die als Argumente übergeben werden müssen. im Ordner "Arbeit" nicht vorhanden. Die IDE kann z. B. einen Aufruf von ausgeben der [SccCheckout](../extensibility/scccheckout-function.md) oder [SccUncheckout](../extensibility/sccuncheckout-function.md) auf eine Datei, die im Ordner "Arbeit" nicht vorhanden, aber im Quellcodeverwaltungssystem vorhanden ist. Dieser Aufruf erfolgreich ausgeführt werden kann. Nur, wenn es keine Datei im Ordner "Arbeit" oder in das Quellcodeverwaltungssystem ist muss die Funktion fehl.  
  
 Bestimmte Funktionen wie `SccAdd` und `SccCheckin`, sollte insbesondere zurückgeben `SCC_E_FILENOTEXIST` Wenn die Datei im Ordner "Arbeit" ist nicht vorhanden. Anderer Funktionen, die voraussichtlich erfolgreich, wenn die Arbeitsdatei nicht vorhanden ist, wenn die Funktionen auf einen gültigen Dateinamen in das Quellcodeverwaltungssystem einsetzen.  
  
 Die Datenquellen-Steuerelement-Plug-in sollten keine Annahmen bezüglich der Berechtigungen für eine Datei in den Arbeitsordner vornehmen, auch wenn das plug-in die Datei schreibgeschützt sind und bei einigen Vorgängen während markiert hätten. Eine Datei im Ordner "Arbeit" kann verschoben, gelöscht und außerhalb der Plug-in des Steuerelements geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)