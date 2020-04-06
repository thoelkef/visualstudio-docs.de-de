---
title: SccUninitialize-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700226"
---
# <a name="sccuninitialize-function"></a>SccUninitialize-Funktion
Diese Funktion bereinigt alle Zuweisungen oder offenen Verbindungen, die durch einen vorherigen Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md) erstellt wurden, um das Quellsteuerungs-Plug-In herunterzufahren.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Der Zeiger auf die Quellsteuerungs-Plug-In-Kontextstruktur, die in Der [sccInitialize](../extensibility/sccinitialize-function.md)erstellt wurde.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Bereinigung wurde erfolgreich abgeschlossen.|

## <a name="remarks"></a>Bemerkungen
 Das Quellcodeverwaltungs-Plug-In ist für die Vorbereitung auf das Herunterfahren und das Freilassen von Speicher verantwortlich, den das Plug-In für die Kontextstruktur reserviert hat. Die Funktion wird einmal für jede instanz eines Plug-Ins aufgerufen. Ein Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md) geht diesem Aufruf voraus. Zum Zeitpunkt des Aufrufs von `SccUninitialize`können noch keine Projekte geöffnet sein.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
