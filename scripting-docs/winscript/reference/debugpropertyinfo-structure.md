---
title: DebugPropertyInfo-Struktur | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9baade1a742a06c952906c05c574e752806bc9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640810"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo-Struktur
Beschreibt ein Objekt von einer hierarchischen Struktur, die Namen, Typ und Wert verfügt. Es dient zum Beschreiben der Debugeigenschaften des lokalen Variablen, Parameter, Überwachungsfenster Variablen und Ausdrücke und registriert.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Member  
 dwValidFields  
 Enumerierten Datentyps verwendet, um anzugeben, welche Felder initialisiert werden.  
  
 bstrName  
 Der Eigenschaftsname in einem Kontext.  
  
 bstrType  
 Der Eigenschaftentyp als formatierte Zeichenfolge.  
  
 bstrValue  
 Der Eigenschaftswert als formatierte Zeichenfolge.  
  
 bstrFullName  
 Der vollständige Name der Eigenschaft.  
  
 dwAttrib  
 Eine Enumeration, die die Flags für die Debug-Eigenschaftenattribute angibt.  
  
 pDebugProp  
 Die `IDebugProperty` beschrieben werden, indem Sie die Informationen in diesem `DebugPropertyInfo` Struktur.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)