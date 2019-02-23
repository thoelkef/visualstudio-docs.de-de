---
title: SccQueryChanges-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d21dfe4418d033776431f4864f46412a798be204
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711708"
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