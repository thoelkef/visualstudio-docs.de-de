---
title: "IDebugSymbolProviderDirect::GetMethodFromAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugSymbolProviderDirect::GetMethodFromAddress"
  - "GetMethodFromAddress"
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft Informationen über die Methode auf dem angegebenen debuggen Adresse ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```c#  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### Parameter  
 `pAddress`  
 \[in\]  Debuggen Adresse, die von der [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle dargestellt wird.  
  
 `pGuid`  
 \[out\]  Eindeutiger Bezeichner des Moduls.  
  
 `pAppID`  
 \[out\]  Bezeichner der Anwendungsdomäne.  
  
 `pTokenClass`  
 \[out\]  Token, das die enthaltende Klasse darstellt.  
  
 `pTokenMethod`  
 \[out\]  Token, das das Modul darstellt.  
  
 `pdwOffset`  
 \[out\]  Ein Offset in Bytes vom Anfang des `pAddress`\-Parameters.  
  
 `pdwVersion`  
 \[out\]  Versionsnummer der Methode.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)