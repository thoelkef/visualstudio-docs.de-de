---
title: Scriptgctype-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fce16c756cf06c8cf01937114402832570a0cd3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574394"
---
# <a name="scriptgctype-enumeration"></a>SCRIPTGCTYPE-Enumeration
Der Typ der auszuführenden Garbage Collection. Wird in der [iactivescriptgarbagecollector:: CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) -Methode verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Enumerationswerte  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|Normale Garbage Collection. Der ganzzahlige Wert ist 0.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Führen Sie umfassende Garbage Collection aus. Der ganzzahlige Wert ist 1.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Fehlercodes für Active Script](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)