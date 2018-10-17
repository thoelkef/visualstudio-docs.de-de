---
title: SccGetVersion-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4f2df5db784213d6404253b885d5933de120c7b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230060"
---
# <a name="sccgetversion-function"></a>SccGetVersion-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Funktion ruft die Versionsnummer der Source-Plug-in-API von das Quellcodeverwaltungs-Plug-in unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)

