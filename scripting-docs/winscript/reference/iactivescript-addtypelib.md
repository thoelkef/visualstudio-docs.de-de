---
title: "IActiveScript::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_AddTypeLib"
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddTypeLib
Fügt eine Typbibliothek dem Namespace für das Skript hinzu.  Dies ist mit den `#include`\-Direktive in C\/C\+\+ ähnlich.  Es ermöglicht einen Satz vordefinierter Elemente wie Klassendefinitionen, `typedefs` und die Laufzeitumgebung hinzugefügt werden, benannter Konstanten, die dem Skript verfügbar ist.  
  
## Syntax  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### Parameter  
 `guidTypeLib`  
 \[in\] CLSID der Typbibliothek hinzuzufügen.  
  
 `dwMaj`  
 \[in\] Hauptversionsnummer.  
  
 `dwMin`  
 \[in\] Nebenversionsnummer.  
  
 `dwFlags`  
 \[in\] Optionsflags.  Als kann Folgendes:  
  
|Wert|Bedeutung|  
|----------|---------------|  
|SCRIPTTYPELIB\_ISCONTROL|Die Typbibliothek beschreibt ein ActiveX\-Steuerelement, das vom Host verwendet wird.|  
  
## Rückgabewert  
 Gibt eine der folgenden Werte:  
  
|Rückgabewert|Bedeutung|  
|------------------|---------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet \(beispielsweise, ist das Skriptmodul noch nicht geladen wurde oder initialisiert wurden\).|  
|`TYPE_E_CANTLOADLIBRARY`|Die angegebene Typbibliothek konnte nicht geladen werden.|  
  
## Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)