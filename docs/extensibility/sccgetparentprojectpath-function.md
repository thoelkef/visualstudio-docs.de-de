---
title: SccGetParentProjectPath-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700714"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath-Funktion
Diese Funktion bestimmt den übergeordneten Projektpfad eines angegebenen Projekts. Diese Funktion wird aufgerufen, wenn der Benutzer ein Visual Studio-Projekt zur Quellcodeverwaltung hinzufügt.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Parameter
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpUser

[in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des NULL-Terminators).

 lpProjPath

[in] Zeichenfolge, die den Projektpfad identifiziert (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

 lpAuxProjPath

[in, out] Hilfszeichenfolge zur Identifizierung des Projekts (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

 lpParentProjPath

[in, out] Ausgabezeichenfolge, die den übergeordneten Projektpfad identifiziert (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Der übergeordnete Projektpfad wurde erfolgreich abgerufen.|
|SCC_E_INITIALIZEFAILED|Das Projekt konnte nicht initialisiert werden.|
|SCC_E_INVALIDUSER|Der Benutzer konnte sich nicht beim Quellcodeverwaltungs-Plug-In anmelden.|
|SCC_E_UNKNOWNPROJECT|Project ist dem Quellcodeverwaltungs-Plug-In unbekannt.|
|SCC_E_INVALIDFILEPATH|Ungültiger oder nicht verwendbarer Dateipfad.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_PROJSYNTAXERR|Ungültige Projektsyntax.|
|SCC_E_CONNECTIONFAILURE|Verbindungsproblem speichern.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion gibt einen Erfolgs- oder Fehlercode zurück `lpParentProjPath` und füllt die Variable im Erfolgsfall mit dem vollständigen Projektpfad zum angegebenen Projekt.

 Diese Funktion gibt den übergeordneten Projektpfad eines vorhandenen Projekts zurück. Für das Stammprojekt gibt die Funktion den übergebenen Projektpfad zurück (d. h. denselben Stammprojektpfad). Beachten Sie, dass ein Projektpfad eine Zeichenfolge ist, die nur für das Quellcodeverwaltungs-Plug-In sinnvoll ist.

 Die IDE ist bereit, `lpUser` auch `lpAuxProjPath` Änderungen an den und Parametern zu akzeptieren. Die IDE behält diese Zeichenfolgen bei und übergibt sie an [das SccOpenProject,](../extensibility/sccopenproject-function.md) wenn der Benutzer dieses Projekt in Zukunft öffnet. Diese Zeichenfolgen bieten daher eine Möglichkeit für das Quellcodeverwaltungs-Plug-In, Informationen nachzuverfolgen, die es einem Projekt zuordnen muss.

 Diese Funktion ähnelt dem [SccGetProjPath](../extensibility/sccgetprojpath-function.md), mit der Ausnahme, dass der Benutzer nicht aufgefordert wird, ein Projekt auszuwählen. Es erstellt auch nie ein neues Projekt, sondern funktioniert nur mit einem vorhandenen Projekt.

 Wann `SccGetParentProjectPath` wird `lpProjPath` aufgerufen, ist `lpAuxProjPath` nicht leer und entspricht einem gültigen Projekt. Diese Zeichenfolgen werden in der Regel von `SccGetProjPath` der IDE von einem vorherigen Aufruf der Funktion empfangen.

 Das `lpUser` Argument ist der Benutzername. Die IDE wird mit demselben Benutzernamen übergeben, den `SccGetProjPath` sie zuvor von der Funktion erhalten hat, und das Quellcodeverwaltungs-Plug-In sollte den Namen als Standard verwenden. Wenn der Benutzer bereits über eine offene Verbindung mit dem Plug-In verfügt, sollte das Plug-In versuchen, alle Eingabeaufforderungen zu entfernen, um sicherzustellen, dass die Funktion im Hintergrund funktioniert. Wenn die Anmeldung jedoch fehlschlägt, sollte das Plug-In den Benutzer zur Anmeldung auffordern und, `lpUser`wenn er eine gültige Anmeldung erhält, den Namen in zurückgeben. Da das Plug-In diese Zeichenfolge ändern kann, weist die`SCC_USER_LEN`IDE immer einen Puffer der Größe ( +1) zu. Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmeldename sein (mindestens so gültig wie die alte Zeichenfolge).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technische Hinweise für SccCreateSubProject und SccGetParentProjectPath
 Das Hinzufügen von Projekt- und Projektlösungen zur Quellcodeverwaltung wurde in Visual Studio vereinfacht, um zu minimieren, wie oft ein Benutzer aufgefordert wird, Standorte im Quellcodeverwaltungssystem auszuwählen. Diese Änderungen werden von Visual Studio aktiviert, wenn ein Quellcodeverwaltungs-Plug-In beide neuen `SccGetParentProjectPath` Funktionen, das [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) und die Funktion unterstützt. Der folgende Registrierungseintrag kann jedoch verwendet werden, um diese Änderungen zu deaktivieren und auf das vorherige Verhalten von Visual Studio (Source Control Plug-In-API Version 1.1) zurück:

 **[HKEY_CURRENT_USER-Software-, Microsoft-VisualStudio-8.0-SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Wenn dieser Registrierungseintrag nicht vorhanden ist oder auf dword:00000000 festgelegt ist, versucht Visual Studio, die neuen Funktionen zu verwenden, `SccCreateSubProject`und`SccGetParentProjectPath`.

 Wenn der Registrierungseintrag auf dword:00000001 festgelegt ist, versucht Visual Studio nicht, diese neuen Funktionen zu verwenden, und die Vorgänge des Hinzufügens zur Quellcodeverwaltung funktionieren wie in früheren Versionen von Visual Studio.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
