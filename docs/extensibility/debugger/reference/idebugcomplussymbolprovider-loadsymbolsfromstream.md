---
title: "IDebugComPlusSymbolProvider::LoadSymbolsFromStream | Microsoft Docs"
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
  - "IDebugComPlusSymbolProvider::LoadSymbolsFromStream"
  - "LoadSymbolsFromStream"
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider::LoadSymbolsFromStream
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Lädt die angegebenen Symbole Debuggen der Datenstrom.  
  
## Syntax  
  
```cpp#  
HRESULT LoadSymbolsFromStream(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IStream*  pStream  
);  
```  
  
```c#  
int LoadSymbolsFromStream(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   IStream pStream  
);  
```  
  
#### Parameter  
 `ulAppDomainID`  
 \[in\]  Bezeichner der Anwendungsdomäne.  
  
 `guidModule`  
 \[in\]  Eindeutiger Bezeichner des Moduls.  
  
 `baseAddress`  
 \[in\]  Niedrige Speicheradresse.  
  
 `pUnkMetadataImport`  
 \[in\]  Symbol Objekt, das die Metadaten enthält.  
  
 `pStream`  
 \[in\]  Stream, der die Symbole enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CDebugSymbolProvider\-Objekt** implementiert, das die [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)\-Schnittstelle verfügbar macht.  Die Methode ruft die [LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)\-Methode.  
  
```cpp#  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IStream* pStream  
)  
{  
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);  
}  
```  
  
## Siehe auch  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)