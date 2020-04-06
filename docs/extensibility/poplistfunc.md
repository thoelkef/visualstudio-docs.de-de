---
title: POPLISTFUNC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c5f8c1683a993915476ff23f1f5d5f2c2aba462
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702062"
---
# <a name="poplistfunc"></a>POPLISTFUNC
Dieser Rückruf wird von der IDE an die [SccPopulateList](../extensibility/sccpopulatelist-function.md) übermittelt und vom Quellcodeverwaltungs-Plug-In verwendet, um `SccPopulateList` eine Liste von Dateien oder Verzeichnissen zu aktualisieren (die ebenfalls der Funktion zur Verfügung gestellt werden).

 Wenn ein Benutzer in der IDE den Befehl **Abrufen** auswählt, zeigt die IDE ein Listenfeld aller Dateien an, die der Benutzer abrufen kann. Leider kennt die IDE nicht die genaue Liste aller Dateien, die der Benutzer erhalten könnte; nur das Plug-In hat diese Liste. Wenn andere Benutzer dateienweise zum Quellcodeverwaltungsprojekt hinzugefügt haben, sollten diese Dateien in der Liste angezeigt werden, aber die IDE weiß nichts davon. Die IDE erstellt eine Liste der Dateien, von denen der Benutzer glaubt, dass sie sie erhalten können. Bevor diese Liste dem Benutzer angezeigt wird, ruft es die [SccPopulateList](../extensibility/sccpopulatelist-function.md) `,` auf, die dem Quellcodeverwaltungs-Plug-In die Möglichkeit gibt, Dateien aus der Liste hinzuzufügen und zu löschen.

## <a name="signature"></a>Signatur
 Das Quellcodeverwaltungs-Plug-In ändert die Liste, indem eine IDE-implementierte Funktion mit dem folgenden Prototyp aufgerufen wird:

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>Parameter
 pvCallerData `pvCallerData` Der Parameter, der vom Aufrufer (der IDE) an die [SccPopulateList](../extensibility/sccpopulatelist-function.md)übergeben wurde. Das Quellcodeverwaltungs-Plug-In sollte nichts über den Inhalt dieses Parameters annehmen.

 fAddRemove `TRUE`If `lpFileName` ist eine Datei, die der Dateiliste hinzugefügt werden soll. Wenn `FALSE` `lpFileName` , eine Datei ist, die aus der Dateiliste gelöscht werden soll.

 nStatus Status `lpFileName` von (eine `SCC_STATUS` Kombination der Bits; siehe [Dateistatuscode](../extensibility/file-status-code-enumerator.md) für Details).

 lpFileName Vollständiger Verzeichnispfad des Dateinamens, der der Liste hinzugefügt oder aus der Liste gelöscht werden soll.

## <a name="return-value"></a>Rückgabewert

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`TRUE`|Das Plug-In kann diese Funktion weiterhin aufrufen.|
|`FALSE`|Auf der IDE-Seite ist ein Problem aufgetreten (z. B. eine Nichtspeichersituation). Das Plug-In sollte den Betrieb beenden.|

## <a name="remarks"></a>Bemerkungen
 Für jede Datei, die das Quellcodeverwaltungs-Plug-In der Dateiliste hinzufügen oder aus `lpFileName`der Dateiliste löschen möchte, wird diese Funktion in der übergeben. Das `fAddRemove` Flag zeigt eine neue Datei an, die der Liste hinzugefügt werden soll, oder eine alte Datei, die gelöscht werden soll. Der `nStatus` Parameter gibt den Status der Datei an. Wenn das SCC-Plug-In das Hinzufügen und Löschen von Dateien abgeschlossen hat, wird es vom [SccPopulateList-Aufruf](../extensibility/sccpopulatelist-function.md) zurückgegeben.

> [!NOTE]
> Das `SCC_CAP_POPULATELIST` Funktionsbit ist für Visual Studio erforderlich.

## <a name="see-also"></a>Weitere Informationen
- [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md)
- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [Dateistatuscode](../extensibility/file-status-code-enumerator.md)
