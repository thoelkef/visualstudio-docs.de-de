---
title: SccProperties-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 519a17e7596a9cea479eeb24799724919d49bd45
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56700847"
---
# <a name="sccproperties-function"></a>SccProperties-Funktion
Diese Funktion zeigt die Eigenschaften für eine Datei oder das Projekt der quellcodeverwaltung an.

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

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.

 lpFileName

[in] Der Name der vollqualifizierte Pfad der Datei oder des Projekts.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Eigenschaften wurden erfolgreich angezeigt.|
|SCC_I_RELOADFILE|Das Versionskontrollsystem wurde die Dateieigenschaften geändert, damit die IDE die Datei neu geladen werden soll.|
|SCC_E_PROJNOTOPEN|Das angegebene Projekt wurde nicht in der quellcodeverwaltung geöffnet.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um die Eigenschaften dieser Datei oder eines Projekts anzuzeigen.|
|SCC_E_FILENOTCONTROLLED|Die angegebene Datei oder das Projekt ist nicht unter quellcodeverwaltung.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unbekannter oder allgemeine Fehler ist aufgetreten.|

## <a name="remarks"></a>Hinweise
 Das Quellcodeverwaltungs-Plug-in zeigt die Eigenschaften in ein eigenes Dialogfeld.

 Die Eigenschaften werden durch das Quellcodeverwaltungs-Plug-in definiert und können unterscheidet sich vom aus-Plug-in-Plug-in. Wenn das plug-in des Benutzers zum Ändern der Eigenschaften einer Datei der quellcodeverwaltung zulässt, sollte es zurückgeben `SCC_I_RELOAD` um der IDE zu signalisieren, die diese Datei oder das Projekt neu geladen werden muss.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)