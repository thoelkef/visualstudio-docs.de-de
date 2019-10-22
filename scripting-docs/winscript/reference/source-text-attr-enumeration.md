---
title: SOURCE_TEXT_ATTR-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573007"
---
# <a name="source_text_attr-enumeration"></a>SOURCE_TEXT_ATTR-Enumeration
Beschreiben die Attribute eines einzelnen Zeichens des Quelltexts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|Das Zeichen ist Teil eines sprach Schlüsselworts, z. b. das VBScript-Schlüsselwort `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Das Zeichen ist Teil eines Kommentar Blocks.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Das Zeichen gehört nicht zum Quelltext der kompilierten Sprache. Beispielsweise der HTML-Code, der einen Skriptblock umgibt.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Das Zeichen ist Teil eines sprach Operators. Beispiel: der arithmetische Operator **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Das Zeichen ist Teil einer sprach numerischen Konstante.  Beispielsweise die Konstante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Das Zeichen ist Teil einer sprach Zeichenfolgen-Konstante. Beispielsweise die Zeichenfolge "Hallo Welt".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Das Zeichen gibt den Anfang eines Funktions Blocks an.|  
  
## <a name="remarks"></a>Hinweise  
 In der Regel geben die Methoden `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` und `IActiveScriptDebug::GetScriptTextAttributes` ein Text Attribut pro Zeichen zurück, es sei denn:  
  
- Das GETATTRTYPE_DEPSCAN-Flag ist festgelegt. in diesem Fall gibt die Methode möglicherweise die SOURCETEXT_ATTR_IDENTIFIER-und SOURCETEXT_ATTR_MEMBERLOOKUP-Flags zurück.  
  
- Das GETATTRFLAG_THIS-Flag ist festgelegt. in diesem Fall gibt die Methode möglicherweise das SOURCETEXT_ATTR_THIS-Flag zurück,  
  
- Das GETATTRFLAG_HUMANTEXT-Flag ist festgelegt. in diesem Fall gibt die Methode möglicherweise das SOURCETEXT_ATTR_HUMANTEXT-Flag zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)