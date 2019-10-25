---
title: Sccproperties-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e269727441eebc93cd78b70f11fdb571f111ee8b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720846"
---
# <a name="sccproperties-function"></a>SccProperties-Funktion
Diese Funktion zeigt Quell Code Verwaltungs Eigenschaften für eine Datei oder ein Projekt an.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 HWND

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpFileName

in Der voll qualifizierte Pfadname der Datei oder des Projekts.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Eigenschaften wurden erfolgreich angezeigt.|
|SCC_I_RELOADFILE|Das Versionskontrollsystem hat die Dateieigenschaften geändert, sodass die IDE diese Datei erneut laden soll.|
|SCC_E_PROJNOTOPEN|Das angegebene Projekt wurde nicht in der Quell Code Verwaltung geöffnet.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, die Eigenschaften dieser Datei oder des Projekts anzuzeigen.|
|SCC_E_FILENOTCONTROLLED|Die angegebene Datei oder das angegebene Projekt befindet sich nicht in der Quell Code Verwaltung.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Ein unbekannter oder allgemeiner Fehler ist aufgetreten.|

## <a name="remarks"></a>Hinweise
 Das Quellcodeverwaltungs-Plug-in zeigt die Eigenschaften in einem eigenen Dialogfeld an.

 Die Eigenschaften werden durch das Quellcodeverwaltungs-Plug-in definiert und können sich vom Plug-in zum Plug-in unterscheiden. Wenn das Plug-in es dem Benutzer ermöglicht, die Eigenschaften der Quell Code Verwaltung einer Datei zu ändern, sollte `SCC_I_RELOAD` zurückgegeben werden, um der IDE zu signalisieren, dass diese Datei bzw. das Projekt erneut geladen werden muss.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)