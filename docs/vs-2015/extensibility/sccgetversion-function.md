---
title: Sccgetversion-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200046"
---
# <a name="sccgetversion-function"></a>SccGetVersion-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion Ruft die Versionsnummer der Quellcodeverwaltungs-Plug-in-API ab, die vom Quellcodeverwaltungs-Plug-in unterstützt wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
