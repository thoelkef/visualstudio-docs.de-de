---
title: SccQueryInfo-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e01c76f5696e029cd7d15be75786b1009af4a673
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678630"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo-Funktion
Diese Funktion ruft die Statusinformationen für einen Satz von ausgewählten Dateien unter quellcodeverwaltung.

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
 pvContext

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 nFiles

[in] Anzahl der Dateien im angegebenen der `lpFileNames` Array und die Länge der `lpStatus` Array.

 lpFileNames

[in] Ein Array der Namen von Dateien, die abgefragt werden.

 lpStatus

[in, out] Ein Array, in dem das Quellcodeverwaltungs-Plug-in die Statusflags für jede Datei zurückgegeben werden. Weitere Informationen finden Sie unter [Datei Statuscode](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Abfrage war erfolgreich.|
|SCC_E_ACCESSFAILURE|Es wurde ein Problem mit dem Zugriff auf das Quellcodeverwaltungssystem, die wahrscheinlich von Netzwerk-oder Konflikte verursacht. Eine Wiederholung wird empfohlen.|
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht in der quellcodeverwaltung öffnen.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischen Fehler.|

## <a name="remarks"></a>Hinweise
 Wenn `lpFileName` ist eine leere Zeichenfolge ist, es gibt derzeit keine Informationen zu aktualisieren. Andernfalls ist es der vollständige Pfadname der Datei für die die Statusinformationen geändert haben kann.

 Die return-Array kann eine Bitmaske der werden `SCC_STATUS_xxxx` Bits. Weitere Informationen finden Sie unter [Datei Statuscode](../extensibility/file-status-code-enumerator.md). Ein Quellcodeverwaltungssystem unterstützen möglicherweise nicht alle Bitdatentypen. Z. B. wenn `SCC_STATUS_OUTOFDATE` nicht angeboten wird, wird das Bit nicht festgelegt ist.

 Beachten Sie Folgendes ein, wenn Sie diese Funktion verwenden, checken Sie Dateien, `MSSCCI` Status Anforderungen:

-   `SCC_STATUS_OUTBYUSER` wird festgelegt, wenn der aktuelle Benutzer die Datei ausgecheckt hat.

-   `SCC_STATUS_CHECKEDOUT` kann nicht festgelegt werden, es sei denn, `SCC_STATUS_OUTBYUSER` festgelegt ist.

-   `SCC_STATUS_CHECKEDOUT` Wenn die Datei in das angegebene Arbeitsverzeichnis ausgecheckt ist, wird nur festgelegt werden.

-   Wenn die Datei vom aktuellen Benutzer in einem anderen Verzeichnis als Arbeitsverzeichnis ausgecheckt ist `SCC_STATUS_OUTBYUSER` festgelegt ist, aber `SCC_STATUS_CHECKEDOUT` nicht.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Dateistatuscode](../extensibility/file-status-code-enumerator.md)