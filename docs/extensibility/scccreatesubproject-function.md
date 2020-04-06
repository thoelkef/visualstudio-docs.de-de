---
title: SccCreateSubProject-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701035"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject-Funktion
Diese Funktion erstellt ein Unterprojekt mit dem angegebenen Namen `lpParentProjPath` unter einem vorhandenen übergeordneten Projekt, das durch das Argument angegeben wird.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Parameter
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpUser

[in, out] Der Benutzername (bis zu SCC_USER_SIZE, einschließlich des NULL-Terminators).

 lpParentProjPath

[in] Eine Zeichenfolge, die den Pfad des übergeordneten Projekts identifiziert (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

 lpSubProjName

[in] Der vorgeschlagene Unterprojektname (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

 lpAuxProjPath

[in, out] Hilfszeichenfolge zur Identifizierung des Projekts (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

 lpSubProjPath

[in, out] Ausgabezeichenfolge, die den Pfad für das Teilprojekt identifiziert (bis zu SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Das Teilprojekt wurde erfolgreich erstellt.|
|SCC_E_INITIALIZEFAILED|Übergeordnetes Projekt konnte nicht initialisiert werden.|
|SCC_E_INVALIDUSER|Der Benutzer konnte sich nicht beim Quellcodeverwaltungssystem anmelden.|
|SCC_E_COULDNOTCREATEPROJECT|Ein Teilprojekt kann nicht erstellt werden.|
|SCC_E_PROJSYNTAXERR|Ungültige Projektsyntax.|
|SCC_E_UNKNOWNPROJECT|Das übergeordnete Projekt ist dem Quellcodeverwaltungs-Plug-In unbekannt.|
|SCC_E_INVALIDFILEPATH|Ungültiger oder nicht verwendbarer Dateipfad.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_CONNECTIONFAILURE|Es ist ein Problem mit der Quellsteuerungs-Plug-In-Verbindung vorliegt.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Unterprojekt mit dem Namen bereits vorhanden ist, kann die Funktion den Standardnamen ändern, um einen eindeutigen Namen zu erstellen, z. B. indem sie ihm "_\<Nummer>" hinzufügt. Der Aufrufer muss bereit sein, `lpSubProjPath`Änderungen `lpAuxProjPath`an zu `lpUser`akzeptieren, und . Die `lpSubProjPath` `lpAuxProjPath` und-Argumente werden dann in einem Aufruf des [SccOpenProject](../extensibility/sccopenproject-function.md)verwendet. Sie sollten nicht vom Anrufer bei der Rückkehr geändert werden. Diese Zeichenfolgen bieten eine Möglichkeit für das Quellcodeverwaltungs-Plug-In, Informationen nachzuverfolgen, die es einem Projekt zuordnen muss. Die Aufrufer-IDE zeigt diese beiden Parameter bei der Rückgabe nicht an, da das Plug-In eine formatierte Zeichenfolge verwenden kann, die möglicherweise nicht zum Anzeigen geeignet ist. Die Funktion gibt einen Erfolgs- oder Fehlercode zurück `lpSubProjPath` und füllt im Erfolgsfall die Variable mit dem vollständigen Projektpfad zum neuen Projekt.

 Diese Funktion ähnelt dem [SccGetProjPath](../extensibility/sccgetprojpath-function.md), mit der Ausnahme, dass sie im Hintergrund ein Projekt erstellt, anstatt den Benutzer aufzufordert, eines auszuwählen. Wenn `SccCreateSubProject` die Funktion `lpParentProjName` aufgerufen `lpAuxProjPath` wird und nicht leer ist und einem gültigen Projekt entspricht. Diese Zeichenfolgen werden in der Regel von `SccGetProjPath` der IDE von einem vorherigen Aufruf der Funktion oder des [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)empfangen.

 Das `lpUser` Argument ist der Benutzername. Die IDE wird mit demselben Benutzernamen übergeben, `SccGetProjPath`den sie zuvor von erhalten hatte, und das Quellcodeverwaltungs-Plug-In sollte den Namen als Standard verwenden. Wenn der Benutzer bereits über eine offene Verbindung mit dem Plug-In verfügt, sollte das Plug-In versuchen, alle Eingabeaufforderungen zu entfernen, um sicherzustellen, dass die Funktion im Hintergrund funktioniert. Wenn die Anmeldung jedoch fehlschlägt, sollte das Plug-In den Benutzer zur Anmeldung auffordern und, `lpUser`wenn er eine gültige Anmeldung erhält, den Namen in zurückgeben. Da das Plug-In diese Zeichenfolge ändern kann, weist die IDE immer einen Puffer der Größe zu (SCC_USER_LEN+1 oder SCC_USER_SIZE, der Platz für den Nullabschluss enthält). Wenn die Zeichenfolge geändert wird, muss die neue Zeichenfolge ein gültiger Anmeldename sein (mindestens so gültig wie die alte Zeichenfolge).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Technische Hinweise für SccCreateSubProject und SccGetParentProjectPath
 Das Hinzufügen von Projekt- und Projektlösungen zur Quellcodeverwaltung wurde in Visual Studio vereinfacht, um zu minimieren, wie oft ein Benutzer aufgefordert wird, Standorte im Quellcodeverwaltungssystem auszuwählen. Diese Änderungen werden von Visual Studio aktiviert, `SccCreateSubProject` wenn ein Quellcodeverwaltungs-Plug-In beide neuen Funktionen und `SccGetParentProjectPath`unterstützt. Der folgende Registrierungseintrag kann jedoch verwendet werden, um diese Änderungen zu deaktivieren und auf das vorherige Verhalten von Visual Studio (Source Control Plug-in-API Version 1.1) zurück:

 **[HKEY_CURRENT_USER-Software-, Microsoft-VisualStudio-8.0-SourceControl] "DoNotCreateSolutionRootFolderInSourceControl"=dword:00000001**

 Wenn dieser Registrierungseintrag nicht vorhanden ist oder auf dword:00000000 festgelegt ist, versucht Visual Studio, die neuen Funktionen zu verwenden, `SccCreateSubProject` und `SccGetParentProjectPath`.

 Wenn der Registrierungseintrag auf dword:00000001 festgelegt ist, versucht Visual Studio nicht, diese neuen Funktionen zu verwenden, und die Vorgänge des Hinzufügens zur Quellcodeverwaltung funktionieren wie in früheren Versionen von Visual Studio.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
