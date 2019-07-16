---
title: SccQueryChanges-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e2b1e504bef3ec9507afcddf4f75bc5f697e843
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353505"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges-Funktion
Diese Funktion Listet die angegebenen Dateien mit Informationen zu Änderungen des Computernamens für jede Datei über eine Callback-Funktion.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parameter
 "pContext"

[in] Der Datenquellen-Steuerelement-Plug-in Kontextzeiger.

 nFiles

[in] Anzahl der Dateien im `lpFileNames` Array.

 lpFileNames

[in] Array von Dateinamen, zu dem Informationen abgerufen werden soll.

 pfnCallback

[in] Rückruffunktion für jedes Dateinamen in der Liste (finden Sie unter [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Einzelheiten).

 pvCallerData

[in] Wert, der unverändert an die Rückruffunktion übergeben wird.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Der Abfragevorgang erfolgreich abgeschlossen wurde.|
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht in der quellcodeverwaltung geöffnet.|
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen.|
|SCC_E_NONSPECIFICERROR|Ein Unbekannter oder allgemeiner Fehler aufgetreten.|

## <a name="remarks"></a>Hinweise
 Änderungen, die abgefragt wird, die auf den Namespace sind: insbesondere umbenennen, hinzufügen und Entfernen einer Datei.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Fehlercodes](../extensibility/error-codes.md)