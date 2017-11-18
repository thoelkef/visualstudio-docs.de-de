---
title: SccGetVersion Funktion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetVersion
helpviewer_keywords: SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f64b1412d0750bba4d3985d33286915e22f1474
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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