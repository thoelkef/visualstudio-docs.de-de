---
title: SccGetVersion-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2b3818aaa5097313d9150b365544267768507f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56708939"
---
# <a name="sccgetversion-function"></a>SccGetVersion-Funktion
Diese Funktion ruft die Versionsnummer der Source-Plug-in-API von das Quellcodeverwaltungs-Plug-in unterstützt werden.

## <a name="syntax"></a>Syntax

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>Parameter
 Keine

## <a name="return-value"></a>Rückgabewert
 Ein `LONG` -Datentyp, der die Versionsnummer der unterstützten Datenquellen-Plug-in-API enthält:

|WORD|Beschreibung|
|----------|-----------------|
|HIWORD|Hauptversion|
|LOWORD|Nebenversion|

## <a name="remarks"></a>Hinweise
 Wenn ein Quellcodeverwaltungs-Plug-in Version 1.3 von der Quelle-Plug-in-API unterstützt, würde diese Funktion z. B. 0x0103 zurück.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)