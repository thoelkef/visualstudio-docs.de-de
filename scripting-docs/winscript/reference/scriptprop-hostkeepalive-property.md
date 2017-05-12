---
title: "SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# SCRIPTPROP_HOSTKEEPALIVE-Eigenschaft
Wird verwendet, um anzugeben, ob das Skriptmodul vollständig funktionsfähig gehalten werden sollte, wenn es ausstehende Verweise gibt.  
  
 Verwenden Sie [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md), um diese Eigenschaft zu `true` festzulegen.  Wenn diese Eigenschaft auf `true` festgelegt ist, wird das Skriptmodul alle Funktionen, solange es mindestens einen ausstehenden Verweis entweder auf das Skriptmodul selbst gibt, oder einem `IDispatch` Zeiger auf einen JavaScript\-Objekt geführt, das durch das Skriptmodul erstellt wird, verwendet.  Wenn diese Eigenschaft auf `true` festgelegt wird, sollten Sie das Skriptmodul explizit schließen oder zurückgesetzt werden, indem Sie die [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) oder [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)\-Methoden ausführen.  Die Version des letzten Verweises auf ein Skriptobjekt schließt das Skriptmodul unten.  
  
## Syntax  
  
```  
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## Anforderungen  
 Diese Eigenschaft wird nur in der Version von activscp.idl, das mit [!INCLUDE[win8](../../javascript/includes/win8-md.md)], mit 2707082 KB für Internet Explorer 8 auf [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] oder mit 2722913 KB für Internet Explorer 9 auf [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] oder [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)] installiert ist.