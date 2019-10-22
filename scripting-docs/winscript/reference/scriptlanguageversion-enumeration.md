---
title: Scriptlanguageversion-Enumeration | Microsoft-Dokumentation
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
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574364"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION-Enumeration
Gibt die möglichen Skript Versionen an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Die Standardversion. Der ganzzahlige Wert ist 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting Version 5,7. Der ganzzahlige Wert ist 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting Version 5,8. Der ganzzahlige Wert ist 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Die maximale Version. Der ganzzahlige Wert ist 255.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)