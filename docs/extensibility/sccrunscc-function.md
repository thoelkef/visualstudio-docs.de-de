---
title: SccRunScc-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d012908e59be8b82e34ff68cdab1945c5bd2de8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700398"
---
# <a name="sccrunscc-function"></a>SccRunScc-Funktion
Diese Funktion ruft das Verwaltungstool für die Quellcodeverwaltung auf.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccRunScc(
   LPVOID  pvContext,
   HWND    hWnd,
   LONG    nFiles,
   LPCSTR* lpFileNames
);
```

#### <a name="parameters"></a>Parameter
 pvContext

[in] Die Quellcodeverwaltungs-Plug-In-Kontextstruktur.

 hWnd

[in] Ein Handle für das IDE-Fenster, das das Quellcodeverwaltungs-Plug-In als übergeordnetes Element für alle dialogfelder verwenden kann, die es bereitstellt.

 nFiles

[in] Anzahl der im `lpFileNames` Array angegebenen Dateien.

 lpFileNames

[in] Array ausgewählter Dateinamen.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Das Quellcodeverwaltungsverwaltungstool wurde erfolgreich aufgerufen.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|
|SCC_E_INITIALIZEFAILED|Fehler beim Initialisieren des Quellcodeverwaltungssystems.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quellcodeverwaltungssystem ist ein Problem auftritt, wahrscheinlich aufgrund von Netzwerk- oder Konfliktproblemen.|
|SCC_E_CONNECTIONFAILURE|Fehler beim Herstellen einer Verbindung mit dem Quellcodeverwaltungssystem.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei befindet sich nicht unter Quellcodeverwaltung.|
|SCC_E_NONSPECIFICERROR|Unspezifischer Fehler.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion ermöglicht es dem Aufrufer, über ein externes Administrationstool auf die gesamte Funktionspalette des Quellcodeverwaltungssystems zuzugreifen. Wenn das Quellcodeverwaltungssystem über keine Benutzeroberfläche verfügt, kann das Quellcodeverwaltungs-Plug-In eine Schnittstelle implementieren, um die erforderlichen Verwaltungsfunktionen auszuführen.

 Diese Funktion wird mit einer Anzahl und einem Array von Dateinamen für die aktuell ausgewählten Dateien aufgerufen. Wenn das Administrationstool dies unterstützt, kann die Liste der Dateien verwendet werden, um Dateien in der Verwaltungsschnittstelle vorzuwählen. Andernfalls kann die Liste ignoriert werden.

 Diese Funktion wird in der Regel aufgerufen, wenn der Benutzer den **Startquellsteuerungsserver \<>** aus dem Menü**Dateiquellcodesteuerung** **File** -> auswählt. Diese **Startmenüoption** kann immer deaktiviert oder sogar ausgeblendet werden, indem Sie einen Registrierungseintrag festlegen. Weitere Informationen finden Sie [unter Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins.](../extensibility/internals/how-to-install-a-source-control-plug-in.md) Diese Funktion wird nur aufgerufen, wenn `SCC_CAP_RUNSCC` [SccInitialize](../extensibility/sccinitialize-function.md) das Funktionsbit zurückgibt (siehe [Funktionsflags](../extensibility/capability-flags.md) für Details zu diesem und anderen Funktionsbits).

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Gewusst wie: Installieren eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Funktionsflags](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
