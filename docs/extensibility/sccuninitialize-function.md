---
title: Sccuninitialize-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321f50173e3c1517cc6a431ff74933e1a02ef1d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720129"
---
# <a name="sccuninitialize-function"></a>SccUninitialize-Funktion
Diese Funktion bereinigt alle Zuordnungen oder geöffneten Verbindungen, die durch einen vorherigen [sccinitialize](../extensibility/sccinitialize-function.md) -aufrufungstyp erstellt wurden, um das Quellcodeverwaltungs-Plug-in zu schließen.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parameter
 pvcontext

in Der Zeiger auf die Kontext Struktur des Quellcodeverwaltungs-Plug-ins, die in [sccinitialize](../extensibility/sccinitialize-function.md)erstellt wurde.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Bereinigung wurde erfolgreich abgeschlossen.|

## <a name="remarks"></a>Hinweise
 Das Quellcodeverwaltungs-Plug-in ist dafür verantwortlich, das Herunterfahren vorzubereiten und Arbeitsspeicher freizugeben, den das Plug-in für die Kontext Struktur zugewiesen hat. Die-Funktion wird einmal für jede angegebene Instanz eines Plug-Ins aufgerufen. Ein [sccinitialize](../extensibility/sccinitialize-function.md) -aufruftritt vor diesem-Befehl auf. Zum Zeitpunkt des Aufruf`SccUninitialize` können noch keine Projekte geöffnet werden.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)