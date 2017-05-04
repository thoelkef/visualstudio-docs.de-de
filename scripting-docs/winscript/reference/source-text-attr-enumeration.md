---
title: "SOURCE_TEXT_ATTR-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SOURCE_TEXT_ATTR-Konstanten"
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# SOURCE_TEXT_ATTR-Enumeration
Beschreiben Sie die Attribute eines einzelnen Zeichens des Quelltexts.  
  
## Syntax  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR  
{  
    SOURCETEXT_ATTR_KEYWORD    = 0x0001,  
    SOURCETEXT_ATTR_COMMENT    = 0x0002,  
    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,  
    SOURCETEXT_ATTR_OPERATOR   = 0x0008,  
    SOURCETEXT_ATTR_NUMBER    = 0x0010,  
    SOURCETEXT_ATTR_STRING    = 0x0020,  
    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040  
};  
  
```  
  
## Mitglieder  
  
|Member|Wert|Description|  
|------------|----------|-----------------|  
|SOURCETEXT\_ATTR\_KEYWORD|0x0001|Das Zeichen ist Teil eines Schlüsselworts beispielsweise das VBScriptschlüsselwort `While`.|  
|SOURCETEXT\_ATTR\_COMMENT|0x0002|Das Zeichen ist Teil eines Kommentarblocks.|  
|SOURCETEXT\_ATTR\_NONSOURCE|0x0004|Das Zeichen ist nicht Teil kompilierter Sprachenquelltext.  Beispielsweise das HTML, das einen Skriptblock umgibt.|  
|SOURCETEXT\_ATTR\_OPERATOR|0x0008|Das Zeichen ist Teil eines Sprachenoperators.  Beispiel:, der arithmetische Operator **\+**.|  
|SOURCETEXT\_ATTR\_NUMBER|0x0010|Das Zeichen ist Teil einer numerischen Konstanten der Sprache.  Beispielsweise die konstanten 3,14159.|  
|SOURCETEXT\_ATTR\_STRING|0x0020|Das Zeichen ist Teil einer Sprachenzeichenfolgenkonstante.  Beispielsweise die Zeichenfolge "Hello World".|  
|SOURCETEXT\_ATTR\_FUNCTION\_START|0x0040|Das Zeichen gibt den Anfang eines Funktionsblocks an|  
  
## Hinweise  
 In der Regel `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` und Textattribut der `IActiveScriptDebug::GetScriptTextAttributes` korrekt eine pro Zeichen, es sei denn:  
  
-   Das GETATTRTYPE\_DEPSCAN\-Flag wird festgelegt, in diesem Fall die Methode möglicherweise die SOURCETEXT\_ATTR\_IDENTIFIER\- und SOURCETEXT\_ATTR\_MEMBERLOOKUP\-Flags zurückgibt,  
  
-   Das GETATTRFLAG\_THIS\-Flag wird festgelegt, in diesem Fall die Methode möglicherweise das SOURCETEXT\_ATTR\_THIS\-Flag zurückgibt,  
  
-   Das GETATTRFLAG\_HUMANTEXT\-Flag wird festgelegt, in diesem Fall die Methode möglicherweise das SOURCETEXT\_ATTR\_HUMANTEXT\-Flag zurückgibt.  
  
## Siehe auch  
 [Konstanten, Enumerationen und Strukturen für Active Script\-Debugger](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)