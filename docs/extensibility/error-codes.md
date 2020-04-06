---
title: Fehlercodes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711843"
---
# <a name="error-codes"></a>Fehlercodes
Wenn eine Quellcodeverwaltungs-Plug-In-API-Funktion einen Fehler zurückgibt, wird erwartet, dass es sich um einen der folgenden Fehlercodes handelt. Alle Fehler sind negativ, Warnungen oder Informationsfehlercodes sind positiv, und der Erfolg ist 0.

|Fehlercode|Wert|BESCHREIBUNG|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Plug-In unterstützt das Hinzufügen von Dateien aus der Quellcodeverwaltung in zwei Schritten. Weitere Informationen finden Sie unter [SccSetOption](../extensibility/sccsetoption-function.md).|
|`SCC_I_FILEDIFFERS`|6|Die lokale Datei unterscheidet sich von der Datei in der Quellcodeverwaltungsdatenbank (z. B. [sccDiff](../extensibility/sccdiff-function.md) kann diesen Wert zurückgeben).|
|`SCC_I_RELOADFILE`|5|Die lokale Datei wurde während des Quellcodeverwaltungsvorgangs geändert. Die IDE sollte die Datei nach Möglichkeit neu laden.|
|`SCC_I_FILENOTAFFECTED`|4|Die Datei ist nicht betroffen.|
|`SCC_I_PROJECTCREATED`|3|Das Projekt wurde während des Quellcodeverwaltungsvorgangs erstellt (z. B. während eines Aufrufs von [SccOpenProject,](../extensibility/sccopenproject-function.md) wenn `SCC_OP_CREATEIFNEW` das Flag angegeben wird).|
|`SCC_I_OPERATIONCANCELED`|2|Vorgang wurde abgebrochen.|
|`SCC_I_ADV_SUPPORT`|1|Plug-In unterstützt erweiterte Optionen für den angegebenen Befehl. Weitere Informationen finden Sie unter [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|
|`SCC_OK`|0|Erfolg.|
|`SCC_E_INITIALIZEFAILED`|-1|Fehler: Initialisierung fehlgeschlagen.|
|`SCC_E_UNKNOWNPROJECT`|-2|Fehler: Projekt ist unbekannt.|
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Fehler: Das Projekt konnte nicht erstellt werden.|
|`SCC_E_NOTCHECKEDOUT`|–4|Fehler: Die Datei ist nicht ausgecheckt.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Fehler: Die Datei ist bereits ausgecheckt.|
|`SCC_E_FILEISLOCKED`|-6|Fehler: Die Datei ist gesperrt.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Fehler: Die Datei ist ausschließlich ausgecheckt.|
|`SCC_E_ACCESSFAILURE`|-8|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|`SCC_E_CHECKINCONFLICT`|–9|Fehler: Beim Einchecken ist ein Konflikt aufgetreten.|
|`SCC_E_FILEALREADYEXISTS`|-10|Fehler: Die Datei ist bereits vorhanden.|
|`SCC_E_FILENOTCONTROLLED`|-11|Fehler: Die Datei befindet sich nicht unter Quellcodeverwaltung.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Fehler: Die Datei ist ausgecheckt.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Fehler: Es ist keine angegebene Version vorhanden.|
|`SCC_E_OPNOTSUPPORTED`|-14|Fehler: Der Vorgang wird nicht unterstützt.|
|`SCC_E_NONSPECIFICERROR`|-15|Unspezifischer Fehler.|
|`SCC_E_OPNOTPERFORMED`|-16|Fehler, der Vorgang wurde nicht ausgeführt.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Fehler: Der Typ der Datei, z. B. binär, wird vom Quellcodeverwaltungssystem nicht unterstützt.|
|`SCC_E_VERIFYMERGE`|–18|Die Datei wurde automatisch zusammengeführt, aber nicht überprüft, da die Benutzerüberprüfung aussteht.|
|`SCC_E_FIXMERGE`|-19|Die Datei wurde automatisch zusammengeführt, aber aufgrund eines Zusammenführungskonflikts, der manuell aufgelöst werden muss, nicht eingecheckt.|
|`SCC_E_SHELLFAILURE`|-20|Fehler aufgrund eines Shellfehlers.|
|`SCC_E_INVALIDUSER`|-21|Fehler: Der Benutzer ist ungültig.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Fehler: Das Projekt ist bereits geöffnet.|
|`SCC_E_PROJSYNTAXERR`|-23|Projektsyntaxfehler.|
|`SCC_E_INVALIDFILEPATH`|-24|Fehler: Der Dateipfad ist ungültig.|
|`SCC_E_PROJNOTOPEN`|-25|Fehler: Das Projekt ist nicht geöffnet.|
|`SCC_E_NOTAUTHORIZED`|-26|Fehler: Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|`SCC_E_FILESYNTAXERR`|-27|Dateisyntaxfehler.|
|`SCC_E_FILENOTEXIST`|-28|Fehler, die lokale Datei ist nicht vorhanden.|
|`SCC_E_CONNECTIONFAILURE`|-29|Fehler: Es ist ein Verbindungsfehler aufgetreten.|
|`SCC_E_UNKNOWNERROR`|-30|Unknown error. (Unbekannter Fehler.)|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Der Hintergrundabsicherungsvorgang wird derzeit ausgeführt.|

## <a name="macros-provided-for-quick-checking"></a>Makros für die schnelle Überprüfung vorgesehen

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Bemerkungen
 Alle Quellcodeverwaltungs-Plug-In-API-Funktionen (mit Ausnahme von [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md)und [SccDiff](../extensibility/sccdiff-function.md)) werden voraussichtlich erfolgreich sein, wenn die lokalen Dateien, die als Argumente übergeben werden, nicht im Arbeitsordner vorhanden sind. Die IDE kann z. B. einen Aufruf des [SccCheckout](../extensibility/scccheckout-function.md) oder [SccUncheckouts](../extensibility/sccuncheckout-function.md) für eine Datei ausgeben, die nicht im Arbeitsordner, aber im Quellcodeverwaltungssystem vorhanden ist. Dieser Aufruf würde Erfolgreich sein. Nur wenn sich keine Datei im Arbeitsordner oder im Quellcodeverwaltungssystem befindet, wird die Funktion voraussichtlich fehlschlagen.

 Bestimmte Funktionen, `SccAdd` z. B. und `SccCheckin`, sollten speziell zurückgegeben werden, `SCC_E_FILENOTEXIST` wenn die Datei im Arbeitsordner nicht vorhanden ist. Es wird erwartet, dass andere Funktionen erfolgreich sind, wenn die Arbeitsdatei nicht vorhanden ist, wenn die Funktionen mit einem gültigen Dateinamen im Quellcodeverwaltungssystem ausgeführt werden.

 Das Quellcodeverwaltungs-Plug-In sollte keine Annahmen hinsichtlich der Berechtigungen für eine Datei im Arbeitsordner treffen, auch wenn das Plug-In die Datei während eines Vorgangs schreibgeschützt markiert hatte. Eine Datei im Arbeitsordner kann außerhalb des Plug-Ins verschoben, gelöscht und geändert werden.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
