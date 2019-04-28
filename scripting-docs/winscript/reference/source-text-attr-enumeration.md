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
ms.openlocfilehash: f34121ca50ae2467addb29809e7a3792063642ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840121"
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
|SOURCETEXT_ATTR_KEYWORD|0x0001|Das Zeichen ist Teil einer Sprach-Schlüsselwort, z. B. die VBScript-Schlüsselwort `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|Das Zeichen ist Teil des Kommentars.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|Das Zeichen ist nicht Teil des Quelltexts kompilierte Sprache. Z. B. die HTML-Code, der einen Skriptblock umgibt.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|Das Zeichen ist Teil eines Operators für die Sprache an. Zum Beispiel:, den arithmetischen Operator **+**.|  
|SOURCETEXT_ATTR_NUMBER|0x0010|Das Zeichen ist Teil einer Sprache numerische Konstante.  Beispielsweise die Konstante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|Das Zeichen ist Teil einer Zeichenfolgenkonstante Sprache. Z. B. die Zeichenfolge "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|Das Zeichen zeigt den Beginn eines Blocks der Funktion|  
  
## <a name="remarks"></a>Hinweise  
 In der Regel die `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, und `IActiveScriptDebug::GetScriptTextAttributes` Methoden geben ein Textattribut pro Zeichen zurück, es sei denn:  
  
- Das GETATTRTYPE_DEPSCAN-Flag wird festgelegt, in diesem Fall kann die Methode die Flags SOURCETEXT_ATTR_IDENTIFIER und SOURCETEXT_ATTR_MEMBERLOOKUP zurückgeben wird,  
  
- Das GETATTRFLAG_THIS-Flag wird festgelegt, in diesem Fall kann die Methode das SOURCETEXT_ATTR_THIS-Flag zurückgeben wird,  
  
- Das GETATTRFLAG_HUMANTEXT-Flag wird festgelegt, in diesem Fall kann die Methode das SOURCETEXT_ATTR_HUMANTEXT-Flag zurückgeben.  
  
## <a name="see-also"></a>Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)