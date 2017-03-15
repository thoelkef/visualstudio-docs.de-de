---
title: "IDebugPortRequest2::GetPortName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2::GetPortName"
helpviewer_keywords: 
  - "IDebugPortRequest2::GetPortName"
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen des Anschlusses ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### Parameter  
 `pbstrPortName`  
 \[out\]  Gibt den Namen des Anschlusses zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)\-Schnittstelle wird normalerweise von einem Client Paket \(Debuggen\) zu einem Anschlusslieferanten \(den Server übergeben\) zum Abrufen einer Verbindung mit einem Port.  berücksichtigen die Debug\- Paket und der Port lieferant die möglichen Auswahlmöglichkeiten für den Port.  Wenn eine einfache Zeichenfolge den angegebenen Anschluss beschrieben werden kann, hat die `IDebugPortRequest2::GetPortName`\-Methode über ausreichende Informationen, um die Beziehung zu erstellen.  Andernfalls können zusätzliche Schnittstellen durch den Client bereitgestellt werden, der vom Server mithilfe `IDebugPortRequest2::QueryInterface`abgerufen werden kann.  
  
## Siehe auch  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)