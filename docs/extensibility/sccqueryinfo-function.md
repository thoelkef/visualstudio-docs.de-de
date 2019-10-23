---
title: Sccqueryinfo-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5807eb6b695e140350696436a8bba351687f4a24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720829"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo-Funktion
Diese Funktion ruft Statusinformationen für einen Satz ausgewählter Dateien unter Quell Code Verwaltung ab.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 nnoch

in Die Anzahl der im `lpFileNames` Array angegebenen Dateien und die Länge des `lpStatus` Arrays.

 lpfile-Namen

in Ein Array von Namen von Dateien, die abgefragt werden sollen.

 lpstatus

[in, out] Ein Array, in dem das Quellcodeverwaltungs-Plug-in die Statusflags für jede Datei zurückgibt. Weitere Informationen finden Sie unter [Datei Status Code](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Abfrage war erfolgreich.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, das wahrscheinlich auf Netzwerk-oder Konfliktprobleme zurückzuführen ist. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht unter Quell Code Verwaltung geöffnet.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Hinweise
 Wenn `lpFileName` eine leere Zeichenfolge ist, sind zurzeit keine zu Aktualisier Ende Statusinformationen vorhanden. Andernfalls ist dies der vollständige Pfadname der Datei, für die die Statusinformationen geändert werden können.

 Das Rückgabe Array kann eine Bitmaske von `SCC_STATUS_xxxx` Bits sein. Weitere Informationen finden Sie unter [Datei Status Code](../extensibility/file-status-code-enumerator.md). Ein Quell Code Verwaltungssystem unterstützt möglicherweise nicht alle BITTypen. Wenn `SCC_STATUS_OUTOFDATE` z. b. nicht angeboten wird, wird das-Bit nicht festgelegt.

 Wenn Sie diese Funktion verwenden, um Dateien auszuchecken, beachten Sie die folgenden `MSSCCI` Status Anforderungen:

- `SCC_STATUS_OUTBYUSER` festgelegt wird, wenn der aktuelle Benutzer die Datei ausgecheckt hat.

- `SCC_STATUS_CHECKEDOUT` kann nur festgelegt werden, wenn `SCC_STATUS_OUTBYUSER` festgelegt ist.

- `SCC_STATUS_CHECKEDOUT` wird nur beim Auschecken der Datei in das festgelegte Arbeitsverzeichnis festgelegt.

- Wenn die Datei vom aktuellen Benutzer in einem anderen Verzeichnis als dem Arbeitsverzeichnis ausgecheckt wird, wird `SCC_STATUS_OUTBYUSER` festgelegt, `SCC_STATUS_CHECKEDOUT` aber nicht.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Dateistatuscode](../extensibility/file-status-code-enumerator.md)