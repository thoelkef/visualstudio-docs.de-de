---
title: SccInitialize-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700633"
---
# <a name="sccinitialize-function"></a>SccInitialize-Funktion
Diese Funktion initialisiert das Quellcodeverwaltungs-Plug-In und bietet Funktionen und Grenzen für die integrierte Entwicklungsumgebung (IDE).

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>Parameter
 `ppvContext`

[in] Das Quellcodeverwaltungs-Plug-In kann hier einen Zeiger auf seine Kontextstruktur platzieren.

 `hWnd`

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 `lpCallerName`

[in] Der Name des Programms, das das Quellcodeverwaltungs-Plug-In aufruft.

 `lpSccName`

[in, out] Der Puffer, in dem das Quellcodeverwaltungs-Plug-In `SCC_NAME_LEN`seinen eigenen Namen angibt (nicht zu überschreiten ).

 `lpSccCaps`

[out] Gibt die Fähigkeitsflags des Quellcodeverwaltungs-Plug-Ins zurück.

 `lpAuxPathLabel`

[in, out] Der Puffer, in dem das Quellcodeverwaltungs-Plug-In eine Zeichenfolge abgibt, `lpAuxProjPath` die den vom [SccOpenProject](../extensibility/sccopenproject-function.md) und dem [SccGetProjPath](../extensibility/sccgetprojpath-function.md) zurückgegebenen Parameter beschreibt (nicht zu überschreiten `SCC_AUXLABEL_LEN`).

 `pnCheckoutCommentLen`

[out] Gibt die maximal zulässige Länge für einen Kassenkommentar zurück.

 `pnCommentLen`

[out] Gibt die maximal zulässige Länge für andere Kommentare zurück.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Die Quellcodeverwaltungsinitialisierung war erfolgreich.|
|SCC_E_INITIALIZEFAILED|Das System konnte nicht initialisiert werden.|
|SCC_E_NOTAUTHORIZED|Der Benutzer darf den angegebenen Vorgang nicht ausführen.|
|SCC_E_NONSPECFICERROR|Unspezifisches Versagen; Quellcodeverwaltungssystem wurde nicht initialisiert.|

## <a name="remarks"></a>Bemerkungen
 Die IDE ruft diese Funktion auf, wenn sie das Quellcodeverwaltungs-Plug-In zum ersten Mal lädt. Es ermöglicht der IDE, bestimmte Informationen, z. B. den Namen des Aufrufers, an das Plug-In weiterzugeben. Die IDE erhält auch bestimmte Informationen wie die maximal zulässige Länge für Kommentare und die Funktionen des Plug-Ins zurück.

 Der `ppvContext` Punkt `NULL` zeigt auf einen Zeiger. Das Quellcodeverwaltungs-Plug-In kann eine Struktur für den eigenen Gebrauch `ppvContext`zuweisen und einen Zeiger auf diese Struktur in speichern. Die IDE übergibt diesen Zeiger an jede andere VSSCI-API-Funktion, sodass das Plug-In Kontextinformationen verfügbar hat, ohne auf globalen Speicher zurückzugreifen und mehrere Instanzen des Plug-Ins zu unterstützen. Diese Struktur sollte beim Aufruf der [SccUninitialize](../extensibility/sccuninitialize-function.md) umgangen werden.

 Die `lpCallerName` `lpSccName` und Parameter ermöglichen es der IDE und dem Quellcodeverwaltungs-Plug-In, Namen auszutauschen. Diese Namen können einfach verwendet werden, um zwischen mehreren Instanzen zu unterscheiden, oder sie können tatsächlich in Menüs oder Dialogfeldern angezeigt werden.

 Der `lpAuxPathLabel` Parameter ist eine Zeichenfolge, die als Kommentar verwendet wird, um den zusätzlichen Projektpfad zu identifizieren, der in der Projektmappendatei gespeichert und an das Quellcodeverwaltungs-Plug-In in einem Aufruf des [SccOpenProject](../extensibility/sccopenproject-function.md)übergeben wird. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]verwendet die Zeichenfolge "SourceSafe Project:"; andere Quellcodeverwaltungs-Plug-Ins sollten diese spezielle Zeichenfolge nicht verwenden.

 Der `lpSccCaps` Parameter gibt dem Quellcodeverwaltungs-Plug-In einen Ort zum Speichern von Bitflags, die die Funktionen des Plug-Ins anzeigen. (Eine vollständige Liste der Funktionsbitflags finden Sie unter [Fähigkeitsflags](../extensibility/capability-flags.md)). Wenn das Plug-In beispielsweise plant, Ergebnisse in eine vom Aufrufer bereitgestellte Rückruffunktion zu schreiben, würde das Plug-In das Fähigkeitsbit SCC_CAP_TEXTOUT festlegen. Dies würde der IDE signalisieren, ein Fenster für Versionskontrollergebnisse zu erstellen.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [Funktionsflags](../extensibility/capability-flags.md)
