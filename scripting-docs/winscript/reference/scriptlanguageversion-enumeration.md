---
title: SCRIPTLANGUAGEVERSION-Enumeration | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION-Enumeration
Gibt die möglichen Versionen scripting an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Die Standardversion. Der ganzzahlige Wert ist 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting Version 5.7 aktualisiert. Der ganzzahlige Wert ist 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows-Version 5.8 Skripts. Der ganzzahlige Wert ist 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Die maximale Version. Der ganzzahlige Wert ist 255.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)