---
title: JsRuntimeAttributes-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsRuntimeAttributes
helpviewer_keywords:
- JsRuntimeAttributes enumeration
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a7917ad5468b8d2924526f953ae444c5d8381eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569060"
---
# <a name="jsruntimeattributes-enumeration"></a>JsRuntimeAttributes-Enumeration
Attribute einer Laufzeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum JsRuntimeAttributes;  
```  
  
## <a name="members"></a>Mitglieder  
  
### <a name="values"></a>Werte  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|Die Laufzeit muss eine zuverlässige Skriptunterbrechung unterstützen. Dadurch erhöht sich die Anzahl von Orten, an denen die Laufzeit nach Anforderungen für eine Skriptunterbrechung sucht, wobei etwas Laufzeitleistung eingebüßt wird.|  
|`JsRuntimeAttributeDisableBackgroundWork`|Die Laufzeit führt keine Aufgaben (z. B. Garbage Collection) in Hintergrundthreads aus.|  
|`JsRuntimeAttributeDisableEval`|Die Verwendung des `eval` - oder `function` -Konstruktors löst eine Ausnahme aus.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|Die Laufzeit generiert keinen systemeigenen Code.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|Die Laufzeit aktiviert alle experimentellen Features.|  
|`JsRuntimeAttributeEnableIdleProcessing`|Der Host ruft `JsIdle`auf, um die Leerlaufverarbeitung zu aktivieren. Andernfalls verwaltet die Laufzeit den Arbeitsspeicher noch etwas aggressiver.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|Durch das Aufrufen von `JsSetException` wird auch die Ausnahme an den Skriptdebugger (sofern vorhanden) versendet, wodurch der Debugger die Möglichkeit erhält, den Vorgang bei der Ausnahme zu unterbrechen.|  
|`JsRuntimeAttributeNone`|Keine besonderen Attribute.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)