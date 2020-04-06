---
title: SccGetProjPath-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 281787da3499c081fbbe6f59b7b8175a4dbf24d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700705"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath-Funktion
Diese Funktion fordert den Benutzer zur Eingabe eines Projektpfads auf, bei dem es sich um eine Zeichenfolge handelt, die nur für das Quellcodeverwaltungs-Plug-In sinnvoll ist. Es wird aufgerufen, wenn der Benutzer:

- Erstellen eines neuen Projekts

- Hinzufügen eines vorhandenen Projekts zur Versionskontrolle

- Versuch, ein vorhandenes Versionskontrollprojekt zu finden

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccGetProjPath (
   LPVOID pvContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPSTR  lpProjName,
   LPSTR  lpLocalPath,
   LPSTR  lpAuxProjPath,
   BOOL   bAllowChangePath,
   LPBOOL pbNew
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpUser

[in, out] Der Benutzername (nicht mehr als SCC_USER_SIZE, einschließlich des NULL-Terminators)

 lpProjName

[in, out] Der Name des IDE-Projekts, des Projektarbeitsbereichs oder der Makefile (nicht mehr als SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

 lpLocalPath

[in, out] Der Arbeitsweg des Projekts. Wenn `bAllowChangePath` `TRUE`dies der Fall ist, kann das Quellcodeverwaltungs-Plug-In diese Zeichenfolge ändern (nicht über _MAX_PATH, einschließlich des NULL-Terminators).

 lpAuxProjPath

[in, out] Ein Puffer für den zurückgegebenen Projektpfad (nicht mehr als SCC_PRJPATH_SIZE, einschließlich des NULL-Terminators).

 bAllowChangePath

[in] Wenn dies der Grundist ist, `TRUE`kann das `lpLocalPath` Quellcodeverwaltungs-Plug-In die Zeichenfolge auffordern und ändern.

 pbNeu

[in, out] Der eintreffende Wert gibt an, ob ein neues Projekt erstellt werden soll. Der zurückgegebene Wert gibt den Erfolg beim Erstellen eines Projekts an:

|Eingehend|Interpretation|
|--------------|--------------------|
|TRUE|Der Benutzer kann ein neues Projekt erstellen.|
|FALSE|Der Benutzer erstellt möglicherweise kein neues Projekt.|

|Ausgehend|Interpretation|
|--------------|--------------------|
|TRUE|Ein neues Projekt wurde erstellt.|
|FALSE|Ein vorhandenes Projekt wurde ausgewählt.|

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Das Projekt wurde erfolgreich erstellt oder abgerufen.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen.|
|SCC_E_CONNECTIONFAILURE|Beim Herstellen einer Verbindung mit dem Quellcodeverwaltungssystem ist ein Problem aufgetreten.|
|SCC_E_NONSPECIFICERROR|Es ist ein unbekannter Fehler aufgetreten.|

## <a name="remarks"></a>Bemerkungen
 Der Zweck dieser Funktion besteht darin, `lpProjName` dass `lpAuxProjPath`die IDE die Parameter und . Nachdem das Quellcodeverwaltungs-Plug-In den Benutzer zur Eingabe dieser Informationen aufgefordert hat, werden diese beiden Zeichenfolgen an die IDE zurückübergibt. Die IDE behält diese Zeichenfolgen in ihrer Projektmappendatei bei und übergibt sie an das [SccOpenProject,](../extensibility/sccopenproject-function.md) wenn der Benutzer dieses Projekt öffnet. Diese Zeichenfolgen ermöglichen es dem Plug-In, Informationen zu verfolgen, die einem Projekt zugeordnet sind.

 Wenn die Funktion zum `lpAuxProjPath` ersten Mal aufgerufen wird, wird auf eine leere Zeichenfolge festgelegt. `lProjName`kann auch leer sein, oder es kann den IDE-Projektnamen enthalten, den das Quellcodeverwaltungs-Plug-In verwenden oder ignorieren kann. Wenn die Funktion erfolgreich zurückgegeben wird, gibt das Plug-In die beiden entsprechenden Zeichenfolgen zurück. Die IDE macht keine Annahmen über diese Zeichenfolgen, verwendet sie nicht und erlaubt dem Benutzer nicht, sie zu ändern. Wenn der Benutzer die Einstellungen ändern möchte, ruft die IDE erneut auf `SccGetProjPath` und gibt dieselben Werte ein, die sie beim vorherigen Mal erhalten hatte. Dadurch erhält das Plug-In die vollständige Kontrolle über diese beiden Zeichenfolgen.

 Für `lpUser`kann die IDE einen Benutzernamen übergeben oder einfach in einem Zeiger an eine leere Zeichenfolge übergeben werden. Wenn ein Benutzername vorhanden ist, sollte das Quellcodeverwaltungs-Plug-In ihn als Standard verwenden. Wenn jedoch kein Name übergeben wurde oder die Anmeldung mit dem angegebenen Namen fehlgeschlagen ist, sollte das `lpUser` Plug-In den Benutzer zur Anmeldung auffordern und den Namen zurückgeben, wenn er eine gültige Anmeldung erhält. Da das Plug-In diese Zeichenfolge ändern kann, weist die`SCC_USER_LEN`IDE immer einen Puffer der Größe ( +1) zu.

> [!NOTE]
> Die erste Aktion, die die IDE ausführt, kann ein Aufruf der `SccOpenProject` Funktion oder der `SccGetProjPath` Funktion sein. Daher haben beide einen `lpUser` identischen Parameter, der es dem Quellcodeverwaltungs-Plug-In ermöglicht, den Benutzer zu einem der beiden Zeiten anzumelden. Auch wenn die Rückgabe von der Funktion auf einen Fehler hinweist, muss das Plug-In diese Zeichenfolge mit einem gültigen Anmeldenamen füllen.

 `lpLocalPath`ist das Verzeichnis, in dem der Benutzer das Projekt aufführt. Möglicherweise handelt es sich um eine leere Zeichenfolge. Wenn derzeit kein Verzeichnis definiert ist (wie im Fall eines Benutzers, der versucht, `bAllowChangePath` `TRUE`ein Projekt aus dem Quellcodeverwaltungssystem herunterzuladen) und wenn dies der `lpLocalPath`Fall ist, kann das Quellcodeverwaltungs-Plug-In den Benutzer zur Eingabe auffordern oder eine andere Methode verwenden, um eine eigene Zeichenfolge in zu platzieren. Wenn `bAllowChangePath` `FALSE`dies der Fall ist, sollte das Plug-In die Zeichenfolge nicht ändern, da der Benutzer bereits im angegebenen Verzeichnis arbeitet.

 Wenn der Benutzer ein neues Projekt erstellt, das unter Quellcodeverwaltung gestellt werden soll, wird es `SccGetProjPath` das Quellcodeverwaltungs-Plug-In möglicherweise nicht tatsächlich im Quellcodeverwaltungssystem erstellt. Stattdessen wird die Zeichenfolge zusammen mit einem `pbNew`Wert ungleich Null für zurückübergibt, was darauf hinweist, dass das Projekt im Quellcodeverwaltungssystem erstellt wird.

 Wenn z. B. ein Benutzer im Assistenten für **neues Projekt** in Visual Studio sein Projekt zur Quellcodeverwaltung hinzufügt, ruft Visual Studio diese Funktion auf, und das Plug-In bestimmt, ob es in Ordnung ist, ein neues Projekt im Quellcodeverwaltungssystem zu erstellen, das das Visual Studio-Projekt enthält. Wenn der Benutzer vor Abschluss des Assistenten auf **Abbrechen** klickt, wird das Projekt nie erstellt. Wenn der Benutzer auf **OK** `SccOpenProject`klickt, `SCC_OPT_CREATEIFNEW`ruft Visual Studio , gibt ein , und das quellgesteuerte Projekt wird zu diesem Zeitpunkt erstellt.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
