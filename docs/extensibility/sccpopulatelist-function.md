---
title: Sccpopulatelist-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a2cfdf5a617352d7ba0c2db00e7705343f1eb5e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720871"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList-Funktion
Mit dieser Funktion wird eine Liste der Dateien für einen bestimmten Quell Code Verwaltungs Befehl aktualisiert und der Quell Code Verwaltungsstatus für alle angegebenen Dateien bereitgestellt.

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
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 nausgeführter Befehl

in Der Quell Code Verwaltungs Befehl, der auf alle Dateien im `lpFileNames` Array angewendet wird (Weitere Informationen finden Sie unter [Befehls Code](../extensibility/command-code-enumerator.md) für eine Liste möglicher Befehle).

 nnoch

in Anzahl der Dateien im `lpFileNames` Array.

 lpfile-Namen

in Ein Array von Dateinamen, die der IDE bekannt sind.

 pfnauffüllen

in Die zum Hinzufügen und Entfernen von Dateien aufzurufende IDE-Rückruffunktion (Weitere Informationen finden Sie unter [poplistfunc](../extensibility/poplistfunc.md) ).

 pvcallerdata

in Der Wert, der unverändert an die Rückruffunktion übermittelt werden soll.

 lpstatus

[in, out] Ein Array für das Quellcodeverwaltungs-Plug-in, mit dem die Statusflags für jede Datei zurückgegeben werden.

 f-Optionen

in Befehlsflags (Weitere Informationen finden Sie im Abschnitt "populatelist-Flag" von [Bitflags, die von bestimmten Befehlen verwendet werden](../extensibility/bitflags-used-by-specific-commands.md) ).

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Erfolgreich.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Hinweise
 Diese Funktion untersucht die Liste der Dateien für den aktuellen Status. Er verwendet die `pfnPopulate` Callback-Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht mit den Kriterien für die `nCommand` übereinstimmt. Wenn der Befehl z. b. `SCC_COMMAND_CHECKIN` ist und eine Datei in der Liste nicht ausgecheckt ist, wird der Rückruf verwendet, um den Aufrufer zu informieren. Gelegentlich findet das Quellcodeverwaltungs-Plug-in möglicherweise andere Dateien, die Teil des Befehls sein können, und fügt Sie hinzu. So kann z. b. ein Visual Basic Benutzer eine BMP-Datei Auschecken, die von seinem Projekt verwendet wird, aber nicht in der Visual Basic-Projektdatei angezeigt wird. Ein Benutzer wählt den **Get** -Befehl in der IDE aus. In der IDE wird eine Liste aller Dateien angezeigt, die der Benutzer erhält, aber bevor die Liste angezeigt wird, wird die `SccPopulateList`-Funktion aufgerufen, um sicherzustellen, dass die anzuzeigende Liste auf dem neuesten Stand ist.

## <a name="example"></a>Beispiel
 Die IDE erstellt eine Liste von Dateien, die Sie vom Benutzer erhalten kann. Bevor diese Liste angezeigt wird, ruft Sie die `SccPopulateList`-Funktion auf und gibt dem Quellcodeverwaltungs-Plug-in die Möglichkeit, Dateien in der Liste hinzuzufügen und zu löschen. Durch das Plug-in wird die Liste durch Aufrufen der angegebenen Rückruffunktion geändert (Weitere Informationen finden Sie unter [poplistfunc](../extensibility/poplistfunc.md) ).

 Das Plug-in ruft weiterhin die `pfnPopulate` Funktion auf, mit der Dateien hinzugefügt und gelöscht werden, bis der Vorgang abgeschlossen ist, und dann von der `SccPopulateList`-Funktion zurückgegeben wird. Die IDE kann dann die Liste anzeigen. Das `lpStatus` Array stellt alle Dateien in der ursprünglichen Liste dar, die von der IDE übermittelt wurde. Das Plug-in füllt den Status aller Dateien zusätzlich zur Verwendung der Rückruffunktion aus.

> [!NOTE]
> Ein Quellcodeverwaltungs-Plug-in verfügt immer über die Möglichkeit, direkt von dieser Funktion zurückzukehren und die Liste unverändert zu belassen. Wenn diese Funktion von einem Plug-in implementiert wird, kann dies angegeben werden, indem das `SCC_CAP_POPULATELIST` Capability-Bitflag beim ersten aufzurufen von [sccinitialize](../extensibility/sccinitialize-function.md)festgelegt wird. Standardmäßig sollte das Plug-in immer davon ausgehen, dass es sich bei allen übergebenen Elementen um Dateien handelt. Wenn die IDE jedoch das `SCC_PL_DIR`-Flag im `fOptions`-Parameter festlegt, werden alle übergebenen Elemente als Verzeichnisse betrachtet. Das Plug-in sollte alle Dateien hinzufügen, die zu den Verzeichnissen gehören. Die IDE übergibt nie eine Mischung aus Dateien und Verzeichnissen.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
- [Von bestimmten Befehlen verwendete Bitflags](../extensibility/bitflags-used-by-specific-commands.md)
- [Befehlscode](../extensibility/command-code-enumerator.md)