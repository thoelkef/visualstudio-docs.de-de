---
title: SccPopulateList-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f518413adba1546bcff4f7cf2e62b4563cf1bcc7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700531"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList-Funktion
Diese Funktion aktualisiert eine Liste der Dateien für einen bestimmten Quellcodeverwaltungsbefehl und stellt den Quellcodeverwaltungsstatus für alle angegebenen Dateien bereit.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccPopulateList (
   LPVOID          pvContext,
   enum SCCCOMMAND nCommand,
   LONG            nFiles,
   LPCSTR*         lpFileNames,
   POPLISTFUNC     pfnPopulate,
   LPVOID          pvCallerData,
   LPLONG          lpStatus,
   LONG            fOptions
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 nCommand

[in] Der Quellcodeverwaltungsbefehl, der `lpFileNames` auf alle Dateien im Array angewendet wird (eine Liste möglicher Befehle finden Sie unter [Befehlscode).](../extensibility/command-code-enumerator.md)

 nFiles

[in] Anzahl der Dateien `lpFileNames` im Array.

 lpFileNames

[in] Ein Array von Dateinamen, die der IDE bekannt sind.

 pfnPopulate

[in] Die IDE-Rückruffunktion zum Hinzufügen und Entfernen von Dateien (Details finden Sie unter [POPLISTFUNC).](../extensibility/poplistfunc.md)

 pvCallerData

[in] Wert, der unverändert an die Rückruffunktion übergeben werden soll.

 lpStatus

[in, out] Ein Array für das Quellcodeverwaltungs-Plug-In, um die Statusflags für jede Datei zurückzugeben.

 Foptions

[in] Befehlsflags (detailsdetails informationen finden Sie im Abschnitt "PopulateList-Flag" von [Bitflags,](../extensibility/bitflags-used-by-specific-commands.md) die von bestimmten Befehlen verwendet werden).

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Erfolg.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion untersucht die Liste der Dateien auf ihren aktuellen Status. Es verwendet `pfnPopulate` die Rückruffunktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht den Kriterien für die `nCommand`entspricht. Wenn der Befehl z. B. lautet `SCC_COMMAND_CHECKIN` und eine Datei in der Liste nicht ausgecheckt ist, wird der Rückruf verwendet, um den Anrufer zu informieren. Gelegentlich kann das Quellcodeverwaltungs-Plug-In andere Dateien finden, die Teil des Befehls sein könnten, und sie hinzufügen. Auf diese Weise kann z. B. ein Visual Basic-Benutzer eine BMP-Datei auschecken, die von seinem Projekt verwendet wird, aber nicht in der Visual Basic-Projektdatei angezeigt wird. Ein Benutzer wählt den **Befehl Abrufen** in der IDE aus. Die IDE zeigt eine Liste aller Dateien an, von denen sie glaubt, `SccPopulateList` dass der Benutzer sie erhalten kann, aber bevor die Liste angezeigt wird, wird die Funktion aufgerufen, um sicherzustellen, dass die liste anzuzeigen, die auf dem neuesten Stand ist.

## <a name="example"></a>Beispiel
 Die IDE erstellt eine Liste von Dateien, von denen der Benutzer glaubt, dass sie sie erhalten kann. Bevor diese Liste angezeigt wird, ruft sie die `SccPopulateList` Funktion auf, sodass das Quellcodeverwaltungs-Plug-In Dateien hinzufügen und aus der Liste löschen kann. Das Plug-In ändert die Liste, indem die angegebene Rückruffunktion aufgerufen wird (weitere Informationen finden Sie unter [POPLISTFUNC).](../extensibility/poplistfunc.md)

 Das Plug-In ruft `pfnPopulate` weiterhin die Funktion auf, die Dateien hinzufügt und löscht, bis sie abgeschlossen ist und dann von der `SccPopulateList` Funktion zurückkehrt. Die IDE kann dann ihre Liste anzeigen. Das `lpStatus` Array stellt alle Dateien in der ursprünglichen Liste dar, die von der IDE übergeben wurden. Das Plug-In füllt den Status all dieser Dateien zusätzlich zur Nutzung der Rückruffunktion aus.

> [!NOTE]
> Ein Quellcodeverwaltungs-Plug-In hat immer die Möglichkeit, einfach sofort von dieser Funktion zurückzukehren und die Liste so zu belassen, wie sie ist. Wenn ein Plug-In diese Funktion implementiert, kann `SCC_CAP_POPULATELIST` dies durch Festlegen der Funktion bitflag im ersten Aufruf der [SccInitialize](../extensibility/sccinitialize-function.md)angegeben werden. Standardmäßig sollte das Plug-In immer davon ausgehen, dass es sich bei allen übergebenen Elementen um Dateien handelt. Wenn die IDE jedoch `SCC_PL_DIR` das `fOptions` Flag im Parameter festlegt, sind alle übergebenen Elemente als Verzeichnisse zu betrachten. Das Plug-In sollte alle Dateien hinzufügen, die in die Verzeichnisse gehören. Die IDE wird niemals in einer Mischung aus Dateien und Verzeichnissen übergeben.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)
- [Befehlscode](../extensibility/command-code-enumerator.md)
