---
title: SccDirQueryInfo-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e19b65ea4b3c4cd87b1f9d6a3db9e6f8ae64d16d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332244"
---
# <a name="sccdirqueryinfo-function"></a>SccDirQueryInfo function
Diese Funktion untersucht eine Liste der vollqualifizierten Verzeichnisse für ihren aktuellen Status.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Parameter
 "pContext"

[in] Datenquellen-Steuerelement-Plug-in Context-Struktur.

 nDirs

[in] Die Anzahl der Verzeichnisse, die abgefragt werden sollen.

 lpDirNames

[in] Ein Array von vollqualifizierten Pfade der Verzeichnisse, die abgefragt werden.

 lpStatus

[in, out] Eine Arraystruktur für das Quellcodeverwaltungs-Plug-in, um die Statusflags zurückzugeben (finden Sie unter [Directory Statuscode](../extensibility/directory-status-code-enumerator.md) Einzelheiten).

## <a name="return-value"></a>Rückgabewert
 Die Source-Steuerelement-Plug-in-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Abfrage war erfolgreich.|
|SCC_E_OPNOTSUPPORTED|Das Quellcodeverwaltungssystem wird dieser Vorgang nicht unterstützt.|
|SCC_E_ACCESSFAILURE|Es wurde ein Problem, das Zugriff auf das Quellcodeverwaltungssystem, möglicherweise aufgrund eines Netzwerk-oder-Konflikte bestehen. Eine Wiederholung wird empfohlen.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nicht spezifischen Fehler.|

## <a name="remarks"></a>Hinweise
 Die Funktion füllt das return-Array mit einer Bitmaske von Bits aus der `SCC_DIRSTATUS` Familie (finden Sie unter [Directory Statuscode](../extensibility/directory-status-code-enumerator.md)), einen Eintrag für jedes Verzeichnis erhält. Das Statusarray, die vom Aufrufer zugeordnet ist.

 Die IDE verwendet diese Funktion auf, bevor Sie ein Verzeichnis umbenannt wird, um zu überprüfen, ob das Verzeichnis befindet sich unter quellcodeverwaltung durch Abfragen, ob es sich um eine entsprechende Projekt verfügt. Wenn das Verzeichnis nicht in der quellcodeverwaltung enthalten ist, kann die IDE die richtige Warnung für dem Benutzer bereitstellen.

> [!NOTE]
> Wenn ein Quellcodeverwaltungs-Plug-in entscheidet, die nicht mindestens einer der Statuswerte implementiert, sollte nicht implementierte Bits auf 0 (null) festgelegt werden.

## <a name="see-also"></a>Siehe auch
- [Datenquellen-Steuerelement-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [Directory-Statuscode](../extensibility/directory-status-code-enumerator.md)