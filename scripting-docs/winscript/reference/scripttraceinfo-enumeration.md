---
title: SCRIPTTRACEINFO-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ed2c6566db8209280be7f102a55c7de8cf85c44
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155809"
---
# <a name="scripttraceinfo-enumeration"></a>SCRIPTTRACEINFO-Enumeration
Stellt das Skriptereignis, das Ablaufverfolgung ausgeführt wird. Verwendet die [iactivescriptsitetraceinfo:: Sendscripttraceinfo-Methode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|Der Anfang eines Skripts.|  
|SCRIPTTRACEINFO_SCRIPTEND|Das Ende des Skripts.|  
|SCRIPTTRACEINFO_COMCALLSTART|Der Anfang des COM-Aufruf.|  
|SCRIPTTRACEINFO_COMCALLEND|Das Ende des COM-Aufruf.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|Der Anfang des Objekt-und Arrayerstellung.|  
|SCRIPTTRACEINFO_CREATEOBJEND|Das Ende des Objekt-und Arrayerstellung.|  
|SCRIPTTRACEINFO_GETOBJSTART|Der Beginn eines Aufrufs GetObject.|  
|SCRIPTTRACEINFO_GETOBJEND|Das Ende eines Aufrufs GetObject.|