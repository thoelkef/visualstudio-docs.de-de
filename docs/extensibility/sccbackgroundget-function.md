---
title: SccBackgroundGet-Funktion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701230"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet-Funktion
Diese Funktion ruft aus der Quellcodeverwaltung jede der angegebenen Dateien ohne Benutzerinteraktion ab.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Parameter
 pContext

[in] Der Kontextzeiger für die Quellcodeverwaltung.

 nFiles

[in] Anzahl der im `lpFileNames` Array angegebenen Dateien.

 lpFileNames

[in, out] Array von Namen von Dateien, die abgerufen werden sollen.

> [!NOTE]
> Die Namen müssen vollqualifizierte lokale Dateinamen sein.

 dwFlags

[in] Befehlsflags`SCC_GET_ALL` `SCC_GET_RECURSIVE`( , ).

 dwBackgroundOperationID

[in] Ein eindeutiger Wert, der diesem Vorgang zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Die Quellcodeverwaltungs-Plug-In-Implementierung dieser Funktion wird voraussichtlich einen der folgenden Werte zurückgeben:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|SCC_OK|Operation erfolgreich abgeschlossen.|
|SCC_E_BACKGROUNDGETINPROGRESS|Ein Hintergrundabruf ist bereits im Gange (das Quellcodeverwaltungs-Plug-In sollte dies nur zurückgeben, wenn es keine gleichzeitigen Batchvorgänge unterstützt).|
|SCC_I_OPERATIONCANCELED|Der Vorgang wurde abgebrochen, bevor er abgeschlossen wurde.|

## <a name="remarks"></a>Bemerkungen
 Diese Funktion wird immer für einen Thread aufgerufen, der sich von dem entfernt hat, mit dem das Quellcodeverwaltungs-Plug-In geladen wurde. Es wird nicht erwartet, dass diese Funktion zurückkehrt, bis sie abgeschlossen ist. Es kann jedoch mehrmals mit mehreren Listen von Dateien aufgerufen werden, alle zur gleichen Zeit.

 Die Verwendung `dwFlags` des Arguments ist die gleiche wie die [von SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>Weitere Informationen
- [Quellcodeverwaltungs-Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
