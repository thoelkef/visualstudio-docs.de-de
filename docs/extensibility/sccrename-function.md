---
title: SccRename-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e270d1be9cdf935dbffa7d094fddaecd4f73a02
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710682"
---
# <a name="sccrename-function"></a>SccRename-Funktion
Diese Funktion benennt eine Datei in das Quellcodeverwaltungssystem.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccRename(
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName,
   LPCSTR lpNewName
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.

 lpFileName

[in] Der vollqualifizierte Dateiname der Datei, die umbenannt wird.

 lpNewName

[in] Der vollqualifizierte neue Name. Wenn der Verzeichnispfad abweicht, wurde die Datei aus einem Unterverzeichnis auf einen anderen verschoben.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Der Umbenennungsvorgang wurde erfolgreich abgeschlossen.|
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht in der quellcodeverwaltung öffnen.|
|SCC_E_FILENOTCONTROLLED|Die Datei ist nicht unter quellcodeverwaltung.|
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht autorisiert, um diesen Vorgang abzuschließen.|
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt konnte nicht als Teil der Umbenennung erstellt werden.|
|SCC_E_OPNOTPERFORMED|Der Vorgang wurde nicht ausgeführt.|
|SCC_E_NONSPECIFICERROR|Ein Unbekannter oder allgemeiner Fehler aufgetreten.|

## <a name="remarks"></a>Hinweise
 Diese Funktion kann zum Umbenennen einer Datei, oder es von einem Speicherort in einen anderen verschieben, in das Quellcodeverwaltungssystem verwendet werden. Das Quellcodeverwaltungs-Plug-Ins sollten nicht versuchen, Zugriff auf die Datei auf dem Datenträger. Es obliegt der IDE auf die lokale Datei umbenennen.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)