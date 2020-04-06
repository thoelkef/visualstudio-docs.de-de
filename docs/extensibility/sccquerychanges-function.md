---
title: SccQueryChanges-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700497"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges-Funktion
Diese Funktion listet eine bestimmte Liste von Dateien auf und stellt über eine Rückruffunktion Informationen zu Namensänderungen für jede Datei bereit.

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
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 nFiles

[in] Anzahl der `lpFileNames` Dateien im Array.

 lpFileNames

[in] Array von Dateinamen, über die Informationen abgefragt werden sollen.

 pfnCallback

[in] Rückruffunktion zum Aufrufen jedes Dateinamens in der Liste (Details finden Sie unter [QUERYCHANGESFUNC).](../extensibility/querychangesfunc.md)

 pvCallerData

[in] Wert, der unverändert an die Rückruffunktion übergeben wird.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Abfrageprozess wurde erfolgreich abgeschlossen.|
|SCC_E_PROJNOTOPEN|Das Projekt wurde nicht in der Quellcodeverwaltung geöffnet.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen.|
|SCC_E_NONSPECIFICERROR|Ein nicht angegebener oder allgemeiner Fehler ist aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Die abgefragten Änderungen beziehen sich auf den Namespace: insbesondere das Umbenennen, Hinzufügen und Entfernen einer Datei.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Fehlercodes](../extensibility/error-codes.md)
