---
title: "IApplicationDebugger::CreateInstanceAtDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.CreateInstanceAtDebugger
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::CreateInstanceAtDebugger"
ms.assetid: 6763afac-c86a-4e88-9580-77108fb242fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::CreateInstanceAtDebugger
Ermöglicht die Erstellung von Objekten im Debuggerprozess durch Code, der dem Debugger prozessextern ist.  
  
> [!IMPORTANT]
>  Diese Methode sollte nicht implementiert werden, da sie nicht vertrauenswürdigem Code ermöglicht, beliebige Objekte in einem vertrauenswürdigen Debuggerthread zu erstellen.  
  
## Syntax  
  
```  
HRESULT CreateInstanceAtDebugger(  
   REFCLSID    rclsid,  
   IUnknown*   pUnkOuter,  
   DWORD       dwClsContext,  
   REFIID      riid,  
   IUnknown**  ppvObject  
);  
```  
  
#### Parameter  
 `rclsid`  
 \[in\] Klassenbezeichner \(CLSID\) des zu erstellenden Objekts.  
  
 `pUnkOuter`  
 \[in\] `NULL`, wenn das Objekt nicht als Teil eines Aggregats erstellt wird.  Andernfalls ist `pUnkOuter` ein Zeiger auf die gesamte `IUnknown`\-Schnittstelle des Objekts \(steuernde `IUnknown`\).  
  
 `dwClsContext`  
 \[in\] Kontext für ausgeführten ausführbaren Code.  Die Werte werden aus der Enumeration `CLSCTX` entnommen.  
  
 `riid`  
 \[in\] Der Schnittstellenbezeichner verwendet, um mit dem Objekt zu kommunizieren.  
  
 `ppvObject`  
 \[out\] Die Adresse der Zeigervariablen, die den in `riid` angeforderten Schnittstellenzeiger empfängt.  Nach der erfolgreichen Rückgabe \*`ppvObject` enthält den angeforderten Schnittstellenzeiger.  Nach einem Fehler \*`ppvObject` enthält `NULL`.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Delegaten dieser Methode zu `CoCreateInstance`.  
  
 Die Methode wird derzeit nicht implementiert.  
  
## Siehe auch  
 [IApplicationDebugger\-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)