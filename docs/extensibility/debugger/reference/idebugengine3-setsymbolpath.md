---
title: "IDebugEngine3::SetSymbolPath | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetSymbolPath"
helpviewer_keywords: 
  - "IDebugEngine3::SetSymbolPath"
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Pfad oder die Pfade ab, die für die Debugsymbole gefunden werden.  
  
## Syntax  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```c#  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### Parameter  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`szSymbolSearchPath`|\[in\]  Eine Zeichenfolge, die den Symbolsuchpfad oder die Pfade enthält.  Weitere Informationen finden Sie im Abschnitt „Hinweise“.  Darf nicht NULL sein.|  
|`szSymbolCachePath`|\[in\]  Eine Zeichenfolge, die den lokalen Pfad enthält, wobei Symbole zwischengespeichert werden können.  Darf nicht NULL sein.|  
|`Flags`|\[in\]  Wird nicht verwendet. immer auf 0 festgelegt.|  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## Hinweise  
 Die Zeichenfolge`szSymbolSearchPath` ist eine Liste mit einer oder mehrerer Pfade durch Semikolons getrennt, um nach Symbolen sucht.  Diese Pfade können ein lokaler Pfad, ein UNC\-Format Pfad oder eine URL handeln.  Diese Pfade können eine Mischung verschiedener Typen werden.  Wenn der Pfad einen UNC\-Pfad \(z. B. \\ \\ Symserver \\ symbols\) ist, sollte das Debugmodul ermitteln, ob der Pfad zu einem Symbolserver und in der Lage ist, Symbole von diesem Server zu laden und diese im Pfad zwischenspeichern, der von `szSymbolCachePath`angegeben wird.  
  
 Der Symbolpfad kann einen oder mehrere Speicherorte Cache enthalten.  Cache werden in der Reihenfolge der Priorität, mit der höchsten Priorität zuerst Cache und in getrennten durch \* Symbole aufgelistet.  Beispiele:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 Die [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)\-Methode führt die eigentliche Auslastung der Symbole aus.  
  
## Siehe auch  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)