---
title: SccGetVersion Funktion | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70beb89f13d2f752f3adb0f25e2b370fa272171a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetversion-function"></a>SccGetVersion-Funktion
Diese Funktion ruft die Versionsnummer von der Quelle-Plug-in-API mit dem von der quellcodeverwaltung-Plug-in unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parameter  
 Keine  
  
## <a name="return-value"></a>Rückgabewert  
 Ein `LONG` -Datentyp, der die Versionsnummer der unterstützten Datenquellen-Steuerelement-Plug-in-API enthält:  
  
|WORD|Beschreibung|  
|----------|-----------------|  
|HIWORD|Hauptversion|  
|LOWORD|Nebenversion|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Quellcodeverwaltungs-Plug-in Version 1.3 der Datenquellen-Steuerelement-Plug-in-API unterstützt, würde diese Funktion z. B. 0x0103 zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)