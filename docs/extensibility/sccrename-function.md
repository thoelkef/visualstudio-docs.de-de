---
title: SccRename-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRename
helpviewer_keywords:
- SccRename function
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88a917e43729b3049e488264c260f8455ab08fe4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700432"
---
# <a name="sccrename-function"></a>SccRename-Funktion
Diese Funktion benennt eine Datei im Quellcodeverwaltungssystem um.

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

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpFileName

[in] Der vollqualifizierte Dateiname der umbenannten Datei.

 lpNewName

[in] Der vollqualifizierte neue Name. Wenn der Verzeichnispfad anders ist, wurde die Datei von einem Unterverzeichnis in ein anderes verschoben.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der Umbenennungsvorgang wurde erfolgreich abgeschlossen.|
|SCC_E_PROJNOTOPEN|Das Projekt ist nicht unter Quellcodeverwaltung geöffnet.|
|SCC_E_FILENOTCONTROLLED|Die Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang abzuschließen.|
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt konnte nicht als Teil des Umbenennungsprozesses erstellt werden.|
|SCC_E_OPNOTPERFORMED|Der Vorgang wurde nicht ausgeführt.|
|SCC_E_NONSPECIFICERROR|Ein nicht angegebener oder allgemeiner Fehler ist aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion kann verwendet werden, um eine Datei umzubenennen oder sie von einem Speicherort an einen anderen im Quellcodeverwaltungssystem zu verschieben. Das Quellcodeverwaltungs-Plug-In sollte nicht versuchen, auf die Datei auf dem Datenträger zuzugreifen. Es liegt in der Verantwortung der IDE, die lokale Datei umzubenennen.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
