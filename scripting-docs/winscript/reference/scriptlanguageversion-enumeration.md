---
title: SCRIPTLANGUAGEVERSION-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aab63989d1ae02f7c75fc9c20a14d59e8a05078
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144510"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION-Enumeration
Gibt die möglichen Versionen Skripterstellung.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Die Standardversion. Der ganzzahlige Wert ist 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting Version 5.7. Der ganzzahlige Wert ist 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows-Version 5.8 Skripterstellung. Der ganzzahlige Wert ist 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Die maximale Version. Der ganzzahlige Wert ist 255.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)