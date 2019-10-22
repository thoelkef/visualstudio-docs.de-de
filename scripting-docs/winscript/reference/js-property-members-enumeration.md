---
title: JS_PROPERTY_MEMBERS-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_MEMBERS
apilocation:
- jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3645e95859e2c2b785e01c7ee9a3cbee8155138d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571733"
---
# <a name="js_property_members-enumeration"></a>JS_PROPERTY_MEMBERS-Enumeration
Flags, um den Typ der Informationen anzugeben, die in einer Anforderung für Member eines Objekts zurückzugeben sind.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
enum JS_PROPERTY_MEMBERS{   JS_PROPERTY_MEMBERS_ALL = 0,   JS_PROPERTY_MEMBERS_ARGUMENTS = 1} JS_PROPERTY_MEMBERS;  
```  
  
## <a name="members"></a>Member  
  
### <a name="values"></a>Werte  
  
|-Name|Beschreibung|  
|----------|-----------------|  
|`JS_PROPERTY_MEMBERS_ALL`|Stellt eine Anforderung, alle Member aufzulisten, dar.|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|Stellt eine Anforderung, nur Argumente aufzulisten, dar.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag. h  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)