---
title: Sccgetversion-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700679"
---
# <a name="sccgetversion-function"></a>SccGetVersion-Funktion
Diese Funktion Ruft die Versionsnummer der Quellcodeverwaltungs-Plug-in-API ab, die vom Quellcodeverwaltungs-Plug-in unterstützt wird.

## <a name="syntax"></a>Syntax

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 Ein `LONG` Datentyp, der die Versionsnummer der unterstützten Quellcodeverwaltungs-Plug-in-API enthält:

|WORD|BESCHREIBUNG|
|----------|-----------------|
|HIWORD|Hauptversion|
|LOWORD|Nebenversion|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Quellcodeverwaltungs-Plug-in z. b. Version 1,3 der Quellcodeverwaltungs-Plug-in-API unterstützt, würde diese Funktion 0x0103 zurückgeben.

## <a name="see-also"></a>Weitere Informationen
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
