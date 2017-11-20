---
title: SOURCE_TEXT_ATTR-Enumeration | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f21bbfacc4918ff0e67731d5efd5521f371cbdf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR-Enumeration
Beschreiben die Attribute eines einzelnen Zeichens des Quelltexts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Member  
  
|Member|Wert|Beschreibung|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0 x 0001|Das Zeichen ist Teil einer Programmiersprachen-Schlüsselwort, z. B. das VBScript-Schlüsselwort `While`.|  
|SOURCETEXT_ATTR_COMMENT|0 x 0002|Das Zeichen ist Teil des Kommentars.|  
|SOURCETEXT_ATTR_NONSOURCE|0 x 0004|Das Zeichen ist nicht Teil des Quelltexts kompilierte Language. Z. B. den HTML-Code, der einen Skriptblock umgibt.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Das Zeichen ist Teil eines Operators für die Sprache an. Zum Beispiel:, den arithmetischen Operator  **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Das Zeichen ist Teil einer Sprache numerische Konstante.  Beispielsweise die Konstante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Das Zeichen ist Teil einer Sprache angegebenen Zeichenfolgenkonstante. Z. B. die Zeichenfolge "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0 x 0040|Das Zeichen wird der Start eines Blocks der Funktion|  
  
## <a name="remarks"></a>Hinweise  
 In der Regel die `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, und `IActiveScriptDebug::GetScriptTextAttributes` Methoden ein Textattribut pro Zeichen, zurückgeben, es sei denn:  
  
-   Das GETATTRTYPE_DEPSCAN-Flag wird festgelegt, in diesem Fall kann die Methode die Flags SOURCETEXT_ATTR_IDENTIFIER und SOURCETEXT_ATTR_MEMBERLOOKUP zurück,  
  
-   Das GETATTRFLAG_THIS-Flag wird festgelegt, in diesem Fall kann die Methode das SOURCETEXT_ATTR_THIS-Flag zurück,  
  
-   Das GETATTRFLAG_HUMANTEXT-Flag wird festgelegt, in diesem Fall kann die Methode das SOURCETEXT_ATTR_HUMANTEXT-Flag zurückgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)