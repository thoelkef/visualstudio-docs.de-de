---
title: "IVariantChangeType::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IVariantChangeType::ChangeType"
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IVariantChangeType::ChangeType
Verwendet einen varianten Wert und erstellt eine neue Variante mit einem angegebenen Typ.  
  
## Syntax  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### Parameter  
 `pvarDst`  
 \[in, out\] a\-Variante, um den Wert zu enthalten dargestellt durch `pvarSrc`, wobei der Typ von `vtNew` angegeben.  
  
 `pvarSrc`  
 \[in\] Varianter Wert A, die in einem neuen Typ zu ändern.  
  
 `lcid`  
 \[in\] Der zu verwenden Gebietsschemakontext, wenn die Argumente zu oder von Zeichenfolgen konvertiert werden.  
  
 `vtNew`  
 \[in\] Gibt den Typ an, damit `pvarDst` wird.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Die `pvarDst` und `pvarSrc`\-Argumente sind möglicherweise gleich, in diesem Fall der ursprüngliche Wert überschrieben wird.  Diese Methode führt `pvarDst` zur `VariantClear`\-Funktion, und infolgedessen sollte `pvarDst` auf einen gültigen Wert initialisiert werden.  
  
## Siehe auch  
 [IVariantChangeType\-Schnittstelle](../../winscript/reference/ivariantchangetype-interface.md)