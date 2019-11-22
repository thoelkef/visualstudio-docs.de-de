---
title: Sccrunscc-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e577af3ce70280b81681cb72295c3511dd3ab4a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720538"
---
# <a name="sccrunscc-function"></a>SccRunScc-Funktion
Diese Funktion Ruft das Tool zur Verwaltung der Quell Code Verwaltung auf.

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
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 HWND

in Ein Handle für das IDE-Fenster, das vom Quellcodeverwaltungs-Plug-in als übergeordnetes Element für alle bereitgestellten Dialogfelder verwendet werden kann.

 nnoch

in Anzahl der Dateien, die im `lpFileNames` Array angegeben sind.

 lpfile-Namen

in Array ausgewählter Dateinamen.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Das Tool zur Verwaltung der Quell Code Verwaltung wurde erfolgreich aufgerufen.|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen.|
|SCC_E_INITIALIZEFAILED|Fehler beim Initialisieren des Quell Code Verwaltungssystems.|
|SCC_E_ACCESSFAILURE|Beim Zugriff auf das Quell Code Verwaltungssystem ist ein Problem aufgetreten, wahrscheinlich aufgrund von Netzwerk-oder Konflikt Problemen.|
|SCC_E_CONNECTIONFAILURE|Fehler beim Herstellen einer Verbindung mit dem Quell Code Verwaltungssystem.|
|SCC_E_FILENOTCONTROLLED|Die ausgewählte Datei befindet sich nicht unter Quell Code Verwaltung.|
|SCC_E_NONSPECIFICERROR|Nicht spezifischer Fehler.|

## <a name="remarks"></a>Hinweise
 Diese Funktion ermöglicht es dem Aufrufer, über ein externes Verwaltungs Tool auf den vollständigen Bereich der Funktionen des Quell Code Verwaltungssystems zuzugreifen. Wenn das Quell Code Verwaltungssystem über keine Benutzeroberfläche verfügt, kann das Quellcodeverwaltungs-Plug-in eine Schnittstelle implementieren, um die erforderlichen Verwaltungsfunktionen auszuführen.

 Diese Funktion wird mit einer Anzahl und einem Array von Dateinamen für die aktuell ausgewählten Dateien aufgerufen. Wenn das Verwaltungs Tool dies unterstützt, kann die Datei Liste verwendet werden, um Dateien in der Verwaltungsschnittstelle vorab auszuwählen. Andernfalls kann die Liste ignoriert werden.

 Diese Funktion wird in der Regel aufgerufen, wenn der Benutzer den **\<Quell Code Verwaltungs > Server starten** aus dem Menü **Datei** -> **Quell** Code Verwaltung auswählt. Diese **Start** Menüoption kann immer deaktiviert oder sogar ausgeblendet werden, indem ein Registrierungs Eintrag festgelegt wird. Weitere Informationen finden Sie unter [How to: Installieren Sie ein Quellcodeverwaltungs-Plug-in](../extensibility/internals/how-to-install-a-source-control-plug-in.md), um Details anzuzeigen. Diese Funktion wird nur aufgerufen, wenn [sccinitialize das `SCC_CAP_RUNSCC` funktionsbit](../extensibility/sccinitialize-function.md) zurückgibt (Weitere Informationen zu dieser und anderen Funktions Bits finden Sie unter [funktionsflags](../extensibility/capability-flags.md)).

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [Vorgehensweise: Installieren eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Funktionsflags](../extensibility/capability-flags.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)