---
title: SccAddFromScc-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAddFromScc
helpviewer_keywords:
- SccAddFromScc function
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd32e31330cdce958e463a40a4d92f88b09afb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701251"
---
# <a name="sccaddfromscc-function"></a>SccAddFromScc-Funktion
Diese Funktion ermöglicht es dem Benutzer, nach Dateien zu suchen, die sich bereits im Quellcodeverwaltungssystem befinden, und diese Dateien anschließend zum Teil des aktuellen Projekts zu machen. Diese Funktion kann z. B. eine gemeinsame Headerdatei in das aktuelle Projekt abrufen, ohne die Datei zu kopieren. Das Rückgabearray von `lplpFileNames`Dateien , enthält die Liste der Dateien, die der Benutzer dem IDE-Projekt hinzufügen möchte.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccAddFromScc (
   LPVOID   pvContext,
   HWND     hWnd,
   LPLONG   lpnFiles,
   LPCSTR** lplpFileNames
);
```

### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 lpnFiles

[in, out] Ein Puffer für die Anzahl der Dateien, die hinzugefügt werden. (Dies `NULL` ist, wenn `lplpFileNames` der Speicher, auf den verwiesen wird, freigegeben werden soll. Weitere Informationen finden Sie unter Bemerkungen.)

 lplpFileNames

[in, out] Ein Array von Zeigern auf alle Dateinamen ohne Verzeichnispfade. Dieses Array wird vom Quellcodeverwaltungs-Plug-In zugewiesen und freigegeben. Wenn `lpnFiles` = `lplpFileNames` 1 `NULL`und ist nicht , enthält `lplpFileNames` der Vorname im Array, auf das der Zielordner verweist.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Dateien wurden erfolgreich gefunden und dem Projekt hinzugefügt.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde ohne Wirkung abgebrochen.|
|SCC_I_RELOADFILE|Eine Datei oder ein Projekt muss neu geladen werden.|

## <a name="remarks"></a>Bemerkungen
 Die IDE ruft diese Funktion auf. Wenn das Quellcodeverwaltungs-Plug-In die Angabe eines lokalen `lpnFiles` Zielordners unterstützt, übergibt die IDE = 1 und übergibt den lokalen Ordnernamen an `lplpFileNames`.

 Wenn der Aufruf `SccAddFromScc` der Funktion zurückgegeben wird, hat `lpnFiles` `lplpFileNames`das Plug-In Werte zugewiesen und , der den Speicher für das `lplpFileNames`Dateinamenarray bei Bedarf zuweist (beachten Sie, dass diese Zuordnung den Zeiger in ersetzt). Das Quellcodeverwaltungs-Plug-In ist für das Platzieren aller Dateien im Verzeichnis des Benutzers oder im angegebenen Bezeichnungsordner verantwortlich. Die IDE fügt dann die Dateien zum IDE-Projekt hinzu.

 Schließlich ruft die IDE diese Funktion ein `NULL` `lpnFiles`zweites Mal auf und gibt für ein. Dies wird vom Quellcodeverwaltungs-Plug-In als spezielles Signal interpretiert, um den für das Dateinamen-Array zugewiesenen Speicher in`lplpFileNames``.`

 `lplpFileNames`ist `char ***` ein Zeiger. Das Quellcodeverwaltungs-Plug-In platziert einen Zeiger auf ein Array von Zeigern auf Dateinamen, wodurch die Liste standardmäßig für diese API übergeben wird.

> [!NOTE]
> Die ersten Versionen der VSSCI-API enthielten keine Möglichkeit, das Zielprojekt für die hinzugefügten Dateien anzugeben. Um dies zu ermöglichen, wurde `lplpFIleNames` die Semantik des Parameters verbessert, um ihn zu einem In/Out-Parameter und nicht zu einem Ausgabeparameter zu machen. Wenn nur eine einzelne Datei angegeben wird, d. h. auf den Wert, auf den mit `lpnFiles` = 1 verwiesen wird, enthält das erste Element des `lplpFileNames` Zielordners. Um diese neue Semantik zu `SccSetOption` verwenden, `nOption`ruft die `SCC_OPT_SHARESUBPROJ`IDE die Funktion auf, deren Parameter auf festgelegt ist. Wenn ein Quellcodeverwaltungs-Plug-In die Semantik `SCC_E_OPTNOTSUPPORTED`nicht unterstützt, wird es zurückgegeben. Dadurch wird die Verwendung der Funktion **"Aus Quellcodeverwaltung hinzufügen"** deaktiviert. Wenn ein Plug-In die Funktion **"Aus Quellcodeverwaltung hinzufügen"** unterstützt (`SCC_CAP_ADDFROMSCC`, `SCC_I_SHARESUBPROJOK`muss es die neue Semantik unterstützen und zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
