---
title: Fehlercodes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 220d53db343a90f6e19e0f365c621cbf55186a8c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189981"
---
# <a name="error-codes"></a>Fehlercodes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine Source-Control-Plug-in-API-Funktion einen Fehler zurückgibt, wird erwartet, dass eine der folgenden Fehlercodes werden. Alle Fehler werden Warnungen oder informationsmeldungen Fehlercodes sind positiv, negativ ist, und Erfolg ist 0.  
  
|Fehlercode|Wert|Beschreibung|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|-Plug-in unterstützt das Hinzufügen von Dateien aus der quellcodeverwaltung in zwei Schritten. Weitere Informationen finden Sie unter [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Die lokale Datei unterscheidet sich von der Datei im Quellcode-Verwaltungsdatenbank (z. B. [SccDiff](../extensibility/sccdiff-function.md) möglicherweise diesen Wert zurück).|  
|`SCC_I_RELOADFILE`|5|Lokale Datei wurde während der Quellcodeverwaltungsvorgang geändert; die IDE soll die Datei nach Möglichkeit erneut laden.|  
|`SCC_I_FILENOTAFFECTED`|4|Die Datei ist nicht betroffen.|  
|`SCC_I_PROJECTCREATED`|3|Das Projekt während der Quellcodeverwaltungsvorgang erstellt wurde (z. B. während eines Aufrufs [SccOpenProject](../extensibility/sccopenproject-function.md) beim `SCC_OP_CREATEIFNEW` -Flag angegeben ist).|  
|`SCC_I_OPERATIONCANCELED`|2|Vorgang wurde abgebrochen.|  
|`SCC_I_ADV_SUPPORT`|1|-Plug-in unterstützt erweiterte Optionen für den angegebenen Befehl. Weitere Informationen finden Sie unter [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Erfolgreich.|  
|`SCC_E_INITIALIZEFAILED`|-1|Fehler: Fehler bei der Initialisierung.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Fehler: das Projekt ist unbekannt.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Fehler: das Projekt konnte nicht erstellt werden.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Fehler: die Datei ist nicht ausgecheckt.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Fehler: die Datei ist bereits ausgecheckt.|  
|`SCC_E_FILEISLOCKED`|-6|Fehler: die Datei ist gesperrt.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Fehler: die Datei wird exklusiv ausgecheckt.|  
|`SCC_E_ACCESSFAILURE`|-8|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|  
|`SCC_E_CHECKINCONFLICT`|-9|Fehler: Es wurde ein Konflikt beim Einchecken.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Fehler: die Datei ist bereits vorhanden.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Fehler: die Datei ist nicht unter quellcodeverwaltung.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Fehler: die Datei ausgecheckt ist.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Fehler: Es ist keine Version angegeben.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Fehler: der Vorgang wird nicht unterstützt.|  
|`SCC_E_NONSPECIFICERROR`|-15|Unspezifischer Fehler.|  
|`SCC_E_OPNOTPERFORMED`|-16|Fehler, der Vorgang wurde nicht ausgeführt.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Fehler: der Typ der Datei, z. B. binär, wird von der Quellcodeverwaltungs-System nicht unterstützt.|  
|`SCC_E_VERIFYMERGE`|-18|Datei wurde automatisch zusammengeführt, aber es wurde nicht aktiviert wurde, weil es ausstehende benutzerüberprüfung ist.|  
|`SCC_E_FIXMERGE`|-19|Datei wurde automatisch zusammengeführt, aber nicht in eingecheckt wurde aufgrund eines Zusammenführungskonflikts, das manuell gelöst werden muss.|  
|`SCC_E_SHELLFAILURE`|-20|Fehler aufgrund eines Fehlers der Shell.|  
|`SCC_E_INVALIDUSER`|-21|Fehler: der Benutzer ist ungültig.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Fehler: das Projekt ist bereits geöffnet.|  
|`SCC_E_PROJSYNTAXERR`|-23|Projekt-Syntaxfehler.|  
|`SCC_E_INVALIDFILEPATH`|-24|Fehler: der Dateipfad ist ungültig.|  
|`SCC_E_PROJNOTOPEN`|-25|Fehler: das Projekt ist nicht geöffnet.|  
|`SCC_E_NOTAUTHORIZED`|-26|Fehler: der Benutzer ist nicht zum Ausführen dieses Vorgangs autorisiert.|  
|`SCC_E_FILESYNTAXERR`|-27|Datei-Syntaxfehler.|  
|`SCC_E_FILENOTEXIST`|-28|Fehler, ist die lokale Datei nicht vorhanden.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Fehler: gab es ein Verbindungsfehler.|  
|`SCC_E_UNKNOWNERROR`|-30|Unbekannter Fehler.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Hintergrund-Get-Vorgang wird zurzeit ausgeführt.|  
  
## <a name="macros-provided-for-quick-checking"></a>Für die schnelle Überprüfung der bereitgestellten Makros  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Hinweise  
 Alle Source Control-Plug-in-API-Funktionen (mit Ausnahme der [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), und [SccDiff](../extensibility/sccdiff-function.md)) erfolgreich sein, wenn führen Sie die lokalen Dateien, die als Argumente übergeben werden sollen nicht im Arbeitsverzeichnis vorhanden. Beispielsweise kann die IDE einen Aufruf von ausgeben der [SccCheckout](../extensibility/scccheckout-function.md) oder [SccUncheckout](../extensibility/sccuncheckout-function.md) für eine Datei, die in den Ordner nicht vorhanden, aber im Quellcodeverwaltungssystem vorhanden ist. Dieser Aufruf erfolgreich ausgeführt werden kann. Nur, wenn keine Datei im Arbeitsverzeichnis oder im Quellcodeverwaltungssystem vorhanden ist wird Funktion erwartet fehl.  
  
 Bestimmte Funktionen wie `SccAdd` und `SccCheckin`, sollte insbesondere zurückgeben `SCC_E_FILENOTEXIST` Wenn die Datei im Arbeitsverzeichnis ist nicht vorhanden. Andere Funktionen werden voraussichtlich erfolgreich sein, wenn es sich bei der Arbeitsdatei nicht vorhanden ist, wenn die Funktionen auf einen gültigen Dateinamen in das Quellcodeverwaltungssystem einsetzen.  
  
 Das Quellcodeverwaltungs-Plug-Ins sollten keine Annahmen bezüglich der Berechtigungen für eine Datei im Arbeitsverzeichnis,, selbst wenn das plug-in die Datei schreibgeschützt während eines Vorgangs markiert haben. Eine Datei im Arbeitsverzeichnis kann verschoben, gelöscht und außerhalb des Plug-ins des Steuerelements geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)

