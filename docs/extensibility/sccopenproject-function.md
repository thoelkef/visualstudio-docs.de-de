---
title: SccOpenProject-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbf566e593bb1ddbc31c70de1570d746a14fbdcf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700572"
---
# <a name="sccopenproject-function"></a>SccOpenProject-Funktion
Diese Funktion öffnet ein vorhandenes Quellcodeverwaltungsprojekt oder erstellt ein neues.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccOpenProject (
   LPVOID        pvContext,
   HWND          hWnd,
   LPSTR         lpUser,
   LPCSTR        lpProjName,
   LPCSTR        lpLocalProjPath,
   LPSTR         lpAuxProjPath,
   LPCSTR        lpComment,
   LPTEXTOUTPROC lpTextOutProc,
   LONG          dwFlags
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpUser

[in, out] Der Name des Benutzers (nicht zu überschreiten SCC_USER_SIZE, einschließlich des NULL-Terminators).

 lpProjName

[in] Die Zeichenfolge, die den Namen des Projekts identifiziert.

 lpLocalProjPath

[in] Der Pfad zum Arbeitsordner für das Projekt.

 lpAuxProjPath

[in, out] Eine optionale Hilfszeichenfolge, die das Projekt identifiziert (nicht mehr als SCC_AUXPATH_SIZE, einschließlich des NULL-Terminators).

 lpComment

[in] Kommentieren Sie ein neues Projekt, das erstellt wird.

 lpTextOutProc

[in] Eine optionale Rückruffunktion zum Anzeigen der Textausgabe aus dem Quellcodeverwaltungs-Plug-In.

 dwFlags

[in] Signalisiert, ob ein neues Projekt erstellt werden muss, wenn das Projekt dem Quellcodeverwaltungs-Plug-In unbekannt ist. Wert kann eine `SCC_OP_CREATEIFNEW` Kombination aus und`SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Erfolg bei der Eröffnung des Projekts.|
|SCC_E_INITIALIZEFAILED|Das Projekt konnte nicht initialisiert werden.|
|SCC_E_INVALIDUSER|Der Benutzer konnte sich nicht beim Quellcodeverwaltungssystem anmelden.|
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt war vor dem Aufruf nicht vorhanden.  Das `SCC_OPT_CREATEIFNEW` Flag wurde gesetzt, aber das Projekt konnte nicht erstellt werden.|
|SCC_E_PROJSYNTAXERR|Ungültige Projektsyntax.|
|SCC_E_UNKNOWNPROJECT|Das Projekt ist dem Quellcodeverwaltungs-Plug-In `SCC_OPT_CREATEIFNEW` unbekannt, und das Flag wurde nicht festgelegt.|
|SCC_E_INVALIDFILEPATH|Ungültiger oder nicht verwendbarer Dateipfad.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf diesen Vorgang nicht ausführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen. Es wird ein Wiederholungsversuch empfohlen.|
|SCC_E_NONSPECFICERROR|Ein unspezifischer Fehler; das Quellcodeverwaltungssystem wurde nicht initialisiert.|

## <a name="remarks"></a>Bemerkungen
 Die IDE kann einen Benutzernamen`lpUser`( ) oder einfach einen Zeiger an eine leere Zeichenfolge übergeben. Wenn ein Benutzername vorhanden ist, sollte das Quellcodeverwaltungs-Plug-In ihn als Standard verwenden. Wenn jedoch kein Name übergeben wurde oder die Anmeldung mit dem angegebenen Namen fehlgeschlagen ist, sollte das Plug-In den Benutzer auffordern, sich anzumelden, und den gültigen Namen zurückgeben, `lpUser` wenn er eine gültige Anmeldung`.` erhält. Da das Plug-In die Benutzernamenzeichenfolge ändern kann, weist die IDE immer einen Puffer der Größe zu (`SCC_USER_LEN`+1 oder SCC_USER_SIZE, der Platz für den Nullabschluss enthält).

> [!NOTE]
> Die erste Aktion, die die IDE möglicherweise ausführen `SccOpenProject` muss, kann ein Aufruf der Funktion oder des [SccGetProjPath](../extensibility/sccgetprojpath-function.md)sein. Aus diesem Grund haben beide `lpUser` einen identischen Parameter.

 `lpAuxProjPath`und`lpProjName` werden aus der Lösungsdatei gelesen, oder `SccGetProjPath` sie werden von einem Aufruf an die Funktion zurückgegeben. Diese Parameter enthalten die Zeichenfolgen, die das Quellcodeverwaltungs-Plug-In dem Projekt zugeordnet hat, und sind nur für das Plug-In aussagekräftig. Wenn sich keine solchen Zeichenfolgen in der Projektmappendatei befinden und der `SccGetProjPath` Benutzer nicht zum Durchsuchen aufgefordert `lpAuxProjPath` `lpProjName`wurde (was eine Zeichenfolge durch die Funktion zurückgeben würde), übergibt die IDE leere Zeichenfolgen für beide und und erwartet, dass diese Werte vom Plug-In aktualisiert werden, wenn diese Funktion zurückgegeben wird.

 `lpTextOutProc`ist ein Zeiger auf eine Rückruffunktion, die von der IDE für das Quellcodeverwaltungs-Plug-In bereitgestellt wird, um die Befehlsergebnisausgabe anzuzeigen. Diese Rückruffunktion wird in [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)ausführlich beschrieben.

> [!NOTE]
> Wenn das Quellcodeverwaltungs-Plug-In beabsichtigt, dies zu `SCC_CAP_TEXTOUT` nutzen, muss es das Flag in [SccInitialize](../extensibility/sccinitialize-function.md)gesetzt haben. Wenn dieses Flag nicht gesetzt wurde oder wenn die `lpTextOutProc` IDE `NULL`diese Funktion nicht unterstützt, wird .

 Der `dwFlags` Parameter steuert das Ergebnis für den Fall, dass das zu öffnende Projekt derzeit nicht vorhanden ist. Es besteht aus zwei `SCC_OP_CREATEIFNEW` `SCC_OP_SILENTOPEN`Bitflags und . Wenn das zu öffnende Projekt bereits vorhanden ist, öffnet die Funktion einfach das Projekt und gibt zurück. `SCC_OK` Wenn das Projekt nicht vorhanden `SCC_OP_CREATEIFNEW` ist und das Flag eingeschaltet ist, kann das Quellcodeverwaltungs-Plug-In `SCC_OK`das Projekt im Quellcodeverwaltungssystem erstellen, öffnen und zurückgeben. Wenn das Projekt nicht vorhanden `SCC_OP_CREATEIFNEW` ist und das Flag deaktiviert ist, `SCC_OP_SILENTOPEN` sollte das Plug-In dann nach dem Flag suchen. Wenn dieses Flag nicht eingeschaltet ist, kann das Plug-In den Benutzer zur Eingabe eines Projektnamens auffordern. Wenn dieses Flag eingeschaltet ist, sollte `SCC_E_UNKNOWNPROJECT`das Plug-In einfach zurückgegeben werden.

## <a name="calling-order"></a>Calling Order
 Im normalen Verlauf der Ereignisse wird [SccInitialize](../extensibility/sccinitialize-function.md) zuerst aufgerufen, um eine Quellcodeverwaltungssitzung zu öffnen. Eine Sitzung kann aus `SccOpenProject`einem Aufruf von bestehen, gefolgt von anderen Source Control Plug-In-API-Funktionen, und wird mit einem Aufruf des [SccCloseProject](../extensibility/scccloseproject-function.md)beendet. Solche Sitzungen können mehrmals wiederholt werden, bevor die [SccUninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.

 Wenn das Quellcodeverwaltungs-Plug-In `SCC_CAP_REENTRANT` `SccInitialize`das Bit in festlegt, kann die obige Sitzungssequenz mehrmals parallel wiederholt werden. Verschiedene `pvContext` Strukturen verfolgen die verschiedenen `pvContext` Sitzungen, in denen jede jeweils einem offenen Projekt zugeordnet ist. Basierend auf`pvContext` dem Parameter kann das Plug-In bestimmen, auf welches Projekt in einem bestimmten Aufruf verwiesen wird. Wenn das `SCC_CAP_REENTRANT` Funktionsbit nicht festgelegt ist, sind nicht erneute Quellcodeverwaltungs-Plug-Ins in ihrer Fähigkeit, mit mehreren Projekten zu arbeiten, eingeschränkt.

> [!NOTE]
> Das `SCC_CAP_REENTRANT` Bit wurde in Version 1.1 der Quellcodeverwaltungs-Plug-In-API eingeführt. Sie wird in Version 1.0 nicht festgelegt oder ignoriert, und alle Quellsteuerungs-Plug-Ins der Version 1.0 werden als nicht erneut angenommen.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Einschränkungen für die Längen von Zeichenfolgen](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
