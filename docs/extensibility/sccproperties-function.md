---
title: SccProperties-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700511"
---
# <a name="sccproperties-function"></a>SccProperties-Funktion
Diese Funktion zeigt Quellcodeverwaltungseigenschaften für eine Datei oder ein Projekt an.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpFileName

[in] Der vollqualifizierte Pfadname der Datei oder des Projekts.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Eigenschaften wurden erfolgreich angezeigt.|
|SCC_I_RELOADFILE|Das Versionskontrollsystem hat die Dateieigenschaften geändert, sodass die IDE diese Datei neu laden sollte.|
|SCC_E_PROJNOTOPEN|Das angegebene Projekt wurde in der Quellcodeverwaltung nicht geöffnet.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, Eigenschaften dieser Datei oder dieses Projekts anzuzeigen.|
|SCC_E_FILENOTCONTROLLED|Die angegebene Datei oder das angegebene Projekt befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Ein unbekannter oder allgemeiner Fehler ist aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Das Quellcodeverwaltungs-Plug-In zeigt die Eigenschaften in einem eigenen Dialogfeld an.

 Die Eigenschaften werden durch das Quellcodeverwaltungs-Plug-In definiert und können von Plug-In zu Plug-In abweichen. Wenn das Plug-In dem Benutzer erlaubt, die Quellcodeverwaltungseigenschaften `SCC_I_RELOAD` einer Datei zu ändern, sollte es zurückkehren, um der IDE zu signalisieren, dass diese Datei oder dieses Projekt neu geladen werden muss.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
