---
title: Sccgetversion-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69078200743f30c4ecfedce8e9be05ef9e7ce20b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721482"
---
# <a name="sccgetversion-function"></a>SccGetVersion-Funktion
Diese Funktion Ruft die Versionsnummer der Quellcodeverwaltungs-Plug-in-API ab, die vom Quellcodeverwaltungs-Plug-in unterstützt wird.

## <a name="syntax"></a>Syntax

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 Ein `LONG` Datentyp, der die Versionsnummer der unterstützten Quellcodeverwaltungs-Plug-in-API enthält:

|WORD|Beschreibung|
|----------|-----------------|
|HIWORD|Hauptversion|
|LOWORD|Neben Version|

## <a name="remarks"></a>Hinweise
 Wenn ein Quellcodeverwaltungs-Plug-in z. b. Version 1,3 der Quellcodeverwaltungs-Plug-in-API unterstützt, würde diese Funktion 0x0103 zurückgeben.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)