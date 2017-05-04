---
title: "IDebugProperty-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugProperty-Schnittstelle"
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty-Schnittstelle
Wird verwendet, um eine hierarchische Eigenschaft der Entität zu beschreiben, die gedebuggt wird, die einen Namen, einen Typ und Wert vorhanden ist.  Am häufigsten wird, `IDebugProperty` verwendet, um das Ergebnis der Ausdrucksauswertung, der Anweisungsauswertung oder der Registerauswertung zu beschreiben.  
  
## Methoden in Vtable\-Reihenfolge  
 In der folgenden Tabelle sind die Methoden der `IDebugProperty`\-Schnittstelle an.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Rufen Sie `DebugPropertyInfo` ab, das dieses `IDebugProperty``.` beschreibt|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Ruft die erweiterten Informationen über eine Eigenschaft ab.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Legt den Wert einer Eigenschaft aus einer Zeichenfolge fest.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Listet die Member einer Eigenschaft auf.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Ruft das übergeordnete Element einer Eigenschaft ab.|  
  
## Anforderungen  
 Header: dbgprop.h