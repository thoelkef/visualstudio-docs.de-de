---
title: Sccopenproject-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccOpenProject
helpviewer_keywords:
- SccOpenProject function
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6aa4a715f8d1b87aa831f6a315f07a19e5d4f46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721057"
---
# <a name="sccopenproject-function"></a>SccOpenProject-Funktion
Diese Funktion öffnet ein vorhandenes Quell Code Verwaltungsprojekt oder erstellt ein neues Projekt.

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
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 HWND

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 lpuser

[in, out] Der Name des Benutzers (nicht zu überschreiten SCC_USER_SIZE, einschließlich des NULL-Terminator).

 lpprojname

in Die Zeichenfolge, die den Namen des Projekts identifiziert.

 lplocalprojpath

in Der Pfad zum Arbeitsordner für das Projekt.

 lpauxprojpath

[in, out] Eine optionale zusätzliche Zeichenfolge, die das Projekt identifiziert (nicht zu überschreiten SCC_AUXPATH_SIZE, einschließlich des NULL-Terminator).

 lpcomment

in Kommentieren Sie ein neues Projekt, das erstellt wird.

 lptextoutproc

in Eine optionale Rückruffunktion zum Anzeigen der Textausgabe aus dem Quellcodeverwaltungs-Plug-in.

 dwFlags

in Signalisiert, ob ein neues Projekt erstellt werden muss, wenn das Projekt dem Quellcodeverwaltungs-Plug-in unbekannt ist. Der Wert kann eine Kombination aus `SCC_OP_CREATEIFNEW` und `SCC_OP_SILENTOPEN.`

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Erfolg beim Öffnen des Projekts.|
|SCC_E_INITIALIZEFAILED|Das Projekt konnte nicht initialisiert werden.|
|SCC_E_INVALIDUSER|Der Benutzer konnte sich nicht beim Quell Code Verwaltungssystem anmelden.|
|SCC_E_COULDNOTCREATEPROJECT|Das Projekt war vor dem-Befehl nicht vorhanden.  Das `SCC_OPT_CREATEIFNEW`-Flag wurde festgelegt, aber das Projekt konnte nicht erstellt werden.|
|SCC_E_PROJSYNTAXERR|Ungültige Projekt Syntax.|
|SCC_E_UNKNOWNPROJECT|Das Projekt ist dem Quellcodeverwaltungs-Plug-in unbekannt, und das `SCC_OPT_CREATEIFNEW`-Flag wurde nicht festgelegt.|
|SCC_E_INVALIDFILEPATH|Ungültiger oder nicht verwendbarer Dateipfad.|
|SCC_E_NOTAUTHORIZED|Der Benutzer ist nicht berechtigt, diesen Vorgang auszuführen.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen. Es wird empfohlen, eine Wiederholung auszuführen.|
|SCC_E_NONSPECFICERROR|Ein nicht spezifischer Fehler. das Quell Code Verwaltungssystem wurde nicht initialisiert.|

## <a name="remarks"></a>Hinweise
 In der IDE kann ein Benutzername (`lpUser`) übergeben werden, oder es kann einfach ein Zeiger auf eine leere Zeichenfolge übergeben werden. Wenn ein Benutzername vorhanden ist, sollte das Quellcodeverwaltungs-Plug-in als Standard verwendet werden. Wenn jedoch kein Name übergeben wurde, oder wenn die Anmeldung mit dem angegebenen Namen fehlgeschlagen ist, sollte das Plug-in den Benutzer auffordern, sich anzumelden, und den gültigen Namen in `lpUser` zurückgeben, wenn ein gültiger Anmelde Name `.` wird, da das Plug-in die Benutzernamen Zeichenfolge ändern kann. verwendet die IDE immer einen Puffer der Größe (`SCC_USER_LEN` + 1 oder SCC_USER_SIZE, der Platz für das NULL-Terminator umfasst).

> [!NOTE]
> Die erste Aktion, die die IDE ausführen kann, ist möglicherweise ein Aufrufen der `SccOpenProject`-Funktion oder des [sccgetprojpath](../extensibility/sccgetprojpath-function.md)-Vorgangs. Aus diesem Grund haben beide einen identischen `lpUser`-Parameter.

 `lpAuxProjPath` und `lpProjName` werden aus der Projektmappendatei gelesen, oder Sie werden von einem Rückruf der `SccGetProjPath`-Funktion zurückgegeben. Diese Parameter enthalten die Zeichen folgen, die das Quellcodeverwaltungs-Plug-in dem Projekt zuordnet, und sind nur für das Plug-in sinnvoll. Wenn keine dieser Zeichen folgen in der Projektmappendatei gefunden wird und der Benutzer nicht zum Durchsuchen aufgefordert wurde (was eine Zeichenfolge durch die `SccGetProjPath`-Funktion zurückgeben würde), übergibt die IDE leere Zeichen folgen sowohl für `lpAuxProjPath` als auch für `lpProjName` und erwartet, dass diese Werte durch das Plug-in aktualisiert werden, wenn is-Funktion gibt zurück.

 `lpTextOutProc` ist ein Zeiger auf eine Rückruffunktion, die von der IDE zum Quellcodeverwaltungs-Plug-in bereitgestellt wird, um die Befehls Ergebnis Ausgabe anzuzeigen. Diese Rückruffunktion wird in [lptextoutproc](../extensibility/lptextoutproc.md)ausführlich beschrieben.

> [!NOTE]
> Wenn das Quellcodeverwaltungs-Plug-in diese Vorteile nutzen soll, muss es das `SCC_CAP_TEXTOUT`-Flag in [sccinitialize](../extensibility/sccinitialize-function.md)festgelegt haben. Wenn dieses Flag nicht festgelegt wurde oder die IDE dieses Feature nicht unterstützt, werden `lpTextOutProc` `NULL`.

 Der `dwFlags`-Parameter steuert das Ergebnis im Fall, dass das geöffnete Projekt derzeit nicht vorhanden ist. Sie besteht aus zwei Bitflags, `SCC_OP_CREATEIFNEW` und `SCC_OP_SILENTOPEN`. Wenn das geöffnete Projekt bereits vorhanden ist, öffnet die Funktion das Projekt einfach und gibt `SCC_OK` zurück. Wenn das Projekt nicht vorhanden ist und das `SCC_OP_CREATEIFNEW`-Flag on on ist, kann das Quellcodeverwaltungs-Plug-in das Projekt im Quell Code Verwaltungssystem erstellen, es öffnen und `SCC_OK` zurückgeben. Wenn das Projekt nicht vorhanden ist, und wenn das `SCC_OP_CREATEIFNEW`-Flag deaktiviert ist, sollte das Plug-in das `SCC_OP_SILENTOPEN`-Flag überprüfen. Wenn dieses Flag nicht on ist, fordert das Plug-in den Benutzer möglicherweise auf, einen Projektnamen einzugeben. Wenn dieses Flag auf ON fest steht, sollte das Plug-in einfach `SCC_E_UNKNOWNPROJECT` zurückgeben.

## <a name="calling-order"></a>Aufruf Reihenfolge
 Im normalen Verlauf der Ereignisse wird [sccinitialize](../extensibility/sccinitialize-function.md) zuerst aufgerufen, um eine Quell Code Verwaltungssitzung zu öffnen. Eine Sitzung kann aus einem Aufruf von `SccOpenProject` bestehen, gefolgt von anderen API-Funktionsaufrufen des Quell Code Verwaltungs-Plug-ins und endet mit einem Aufruf von [scccloseproject](../extensibility/scccloseproject-function.md). Solche Sitzungen können mehrmals wiederholt werden, bevor [sccuninitialize](../extensibility/sccuninitialize-function.md) aufgerufen wird.

 Wenn das Quellcodeverwaltungs-Plug-in das `SCC_CAP_REENTRANT` Bit in `SccInitialize` festlegt, kann die obige Sitzungs Sequenz mehrmals parallel wiederholt werden. Verschiedene `pvContext` Strukturen verfolgen die verschiedenen Sitzungen nach, in denen jede `pvContext` jeweils einem geöffneten Projekt zugeordnet ist. Basierend auf dem `pvContext`-Parameter kann das Plug-in bestimmen, auf welches Projekt in einem bestimmten-Befehl verwiesen wird. Wenn das funktionsbit `SCC_CAP_REENTRANT` nicht festgelegt ist, sind nicht wieder eintretende Quellcodeverwaltungs-Plug-ins in der Lage, mit mehreren Projekten zu arbeiten.

> [!NOTE]
> Das `SCC_CAP_REENTRANT` Bit wurde in Version 1,1 der Quellcodeverwaltungs-Plug-in-API eingeführt. Er ist in Version 1,0 nicht festgelegt oder wird ignoriert, und alle Quellcodeverwaltungs-Plug-ins der Version 1,0 werden als nicht wieder eintretig angenommen.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccCloseProject](../extensibility/scccloseproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [Einschränkungen für die Längen von Zeichenfolgen](../extensibility/restrictions-on-string-lengths.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)