---
title: SccGet-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700890"
---
# <a name="sccget-function"></a>SccGet-Funktion
Diese Funktion ruft eine Kopie einer oder mehrerer Dateien zum Anzeigen und Kompilieren, aber nicht zum Bearbeiten ab. In den meisten Systemen werden die Dateien als schreibgeschützt markiert.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Kontextstruktur des Quellcodeverwaltungs-Plug-Ins.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 nFiles

[in] Anzahl der im `lpFileNames` Array angegebenen Dateien.

 lpFileNames

[in] Array voll qualifizierter Namen von Dateien, die abgerufen werden sollen.

 Foptions

[in] Befehlsflags`SCC_GET_ALL` `SCC_GET_RECURSIVE`( , ).

 pvOptions

[in] Quellcodeverwaltung Plug-in-spezifische Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Erfolg des Betriebs.|
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem unterstützt diesen Vorgang nicht.|
|SCC_E_FILEISCHECKEDOUT|Die Datei, die der Benutzer derzeit ausgecheckt hat, kann nicht abbekommen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NOSPECIFIEDVERSION|Es wurde eine ungültige Version oder ein Datum/eine Uhrzeit angegeben.|
|SCC_E_NONSPECIFICERROR|Unspezifisches Versagen; Datei wurde nicht synchronisiert.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diese Operation auszuführen.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird mit einer Anzahl und einem Array von Namen der abzurufenden Dateien aufgerufen. Wenn die IDE `SCC_GET_ALL`das Flag überschreitet, `lpFileNames` bedeutet dies, dass es sich bei den darin enthaltenen Elementen nicht um Dateien, sondern um Verzeichnisse handelt und dass alle Dateien, die unter Quellcodeverwaltung in den angegebenen Verzeichnissen stehen, abgerufen werden sollen.

 Das `SCC_GET_ALL` Flag kann mit `SCC_GET_RECURSIVE` dem Flag kombiniert werden, um alle Dateien in den angegebenen Verzeichnissen und allen Unterverzeichnissen abzurufen.

> [!NOTE]
> `SCC_GET_RECURSIVE`sollte nie ohne `SCC_GET_ALL`übergeben werden. Beachten Sie außerdem, dass, wenn die Verzeichnisse *C:-A* und *C:-A-B* für einen rekursiven Abruf übergeben werden, *C:-A-B* und alle unterverzeichnisse tatsächlich zweimal abgerufen werden. Es liegt in der Verantwortung der IDE – und nicht der Quellsteuerungs-Plug-Ins –, sicherzustellen, dass Duplikate wie diese aus dem Array herausgehalten werden.

 Selbst wenn ein Quellcodeverwaltungs-Plug-In `SCC_CAP_GET_NOUI` das Flag bei der Initialisierung angegeben hat, was darauf hinweist, dass es keine Benutzeroberfläche für einen Get-Befehl hat, kann diese Funktion weiterhin von der IDE aufgerufen werden, um Dateien abzurufen. Das Flag bedeutet einfach, dass die IDE kein Menüelement Abrufen anzeigt und dass vom Plug-In keine Benutzeroberfläche erwartet wird.

## <a name="rename-files-and-sccget"></a>Umbenennen von Dateien und SccGet
 Situation: Ein Benutzer checkt eine Datei aus, z. B. *a.txt*, und ändert sie. Bevor *a.txt* eingecheckt werden kann, benennt ein zweiter Benutzer *a.txt* in *b.txt* in der Quellcodeverwaltungsdatenbank um, checkt *b.txt*aus, nimmt einige Änderungen an der Datei vor und checkt die Datei ein. Der erste Benutzer möchte, dass die vom zweiten Benutzer vorgenommenen Änderungen vorgenommen werden, damit der erste Benutzer seine lokale Version der *datei a.txt* in *b.txt* umbenennt und die Datei abholt. Der lokale Cache, der Versionsnummern nachverfolgt, ist jedoch weiterhin der Ansicht, dass die erste Version von *a.txt* lokal gespeichert ist, sodass die Quellcodeverwaltung die Unterschiede nicht beheben kann.

 Es gibt zwei Möglichkeiten, diese Situation zu beheben, in der der lokale Cache von Quellcodeverwaltungsversionen nicht mehr mit der Quellcodeverwaltungsdatenbank synchronisiert ist:

1. Erlauben Sie nicht, eine Datei in der derzeit ausgecheckten Quellcodeverwaltungsdatenbank umzubenennen.

2. Machen Sie das Äquivalent von "alt löschen" gefolgt von "neu hinzufügen". Der folgende Algorithmus ist eine Möglichkeit, dies zu erreichen.

    1. Rufen Sie die [SccQueryChanges-Funktion](../extensibility/sccquerychanges-function.md) auf, um mehr über die Umbenennung von *a.txt* in *b.txt* in der Quellcodeverwaltungsdatenbank zu erfahren.

    2. Benennen Sie die lokale *dateia.txt* in *b.txt*um.

    3. Rufen `SccGet` Sie die Funktion sowohl für *a.txt* als auch für *b.txt*auf.

    4. Da *a.txt* in der Quellcodeverwaltungsdatenbank nicht vorhanden ist, wird der lokale Versionscache der fehlenden *a.txt-Versionsinformationen* gelöscht.

    5. Die ausgecheckte *b.txt-Datei* wird mit dem Inhalt der lokalen *b.txt-Datei* zusammengeführt.

    6. Die aktualisierte *b.txt-Datei* kann nun eingecheckt werden.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Bitflags, die von bestimmten Befehlen verwendet werden](../extensibility/bitflags-used-by-specific-commands.md)
