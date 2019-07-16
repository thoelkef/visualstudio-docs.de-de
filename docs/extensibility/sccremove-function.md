---
title: SccRemove-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 70413c2e446f8ed226a58eb8ddfe62ede4a1d61f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338619"
---
# <a name="sccremove-function"></a>SccRemove-Funktion
Diese Funktion löscht Dateien vom Quellcodeverwaltungssystem.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle Dialogfelder verwenden kann, die er bereitstellt.

 nFiles

[in] Anzahl der angegebenen Dateien in die `lpFileNames` Array.

 lpFileNames

[in] Array der Namen von voll gekennzeichneter lokaler Pfad von Dateien, die entfernt werden soll.

 lpComment

[in] Der Kommentar, der auf jede entfernte Datei angewendet werden.

 Bestanden

[in] Befehl Flags (nicht verwendeten).

 pvOptions

[in] Quellcodeverwaltungs-plug-in spezifischen Optionen.

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Zum Entfernen war erfolgreich.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei ist nicht unter quellcodeverwaltung.|
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem wird dieser Vorgang nicht unterstützt.|
|SCC_E_ISCHECKEDOUT|Eine Datei kann nicht entfernt werden, da ein Benutzer zurzeit ausgecheckt ist.|
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht zulässig, um diesen Vorgang auszuführen.|
|SCC_E_NONSPECIFICERROR|Unspezifischen Fehlers; Datei wurde nicht entfernt.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde vor Abschluss abgebrochen.|

## <a name="remarks"></a>Hinweise
 Diese Funktion entfernt die Dateien aus dem Quellcodeverwaltungssystem, jedoch nicht von der Festplatte des Benutzers gelöscht.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)