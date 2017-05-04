---
title: "IDebugProperty::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.GetExtendedInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::GetExtendedInfo"
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::GetExtendedInfo
Get erweiterte Informationen für die Eigenschaft.  
  
## Syntax  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### Parameter  
 `cInfos`  
 \[in\] Objekte Anzahl erweiterte Informationen ein.  
  
 `rgguidExtendedInfo`  
 \[in\] Ein Array von `GUID`s wird übergeben, damit mehrere Elemente von erweiterten Informationen gleichzeitig abgerufen werden können.  
  
 `pExtendedInfo`  
 \[out\] Gibt ein Array von s `VARIANT` zurück, das verwendet werden kann, um die erweiterten Eigenschafteninformationen abzurufen.  
  
## Rückgabewert  
 Gibt gültiges `HRESULT`, in der Regel `S_OK` zurück.  
  
## Hinweise  
 Diese Schnittstelle ruft erweiterte Informationen für dieses Objekt ab.  Das API ist, nur mit dem Ziel das Abrufen von Informationen, die nicht auf abgerufen werden unter Verwendung von `IDebugProperty::GetPropertyInfo` besser\).  
  
## Siehe auch  
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)