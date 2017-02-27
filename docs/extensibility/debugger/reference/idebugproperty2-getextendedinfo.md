---
title: "IDebugProperty2::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die erweiterten Informationen für die Eigenschaft.  
  
## Syntax  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### Parameter  
 `guidExtendedInfo`  
 \[in\]  GUID, die den Typ des erweiterten Informationen bestimmt, der abgerufen werden soll.  Weitere Informationen finden Sie in den Hinweisen.  
  
 `pExtendedInfo`  
 \[out\]  Gibt `VARIANT` \(C\+\+\) oder ein Objekt zurück \(C\#\), die verwendet werden können, um die erweiterten Eigenschaft abgerufen werden soll.  Beispielsweise kann dieser Parameter eine `IUnknown`\-Schnittstelle zurück, die für eine [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)\-Schnittstelle abgefragt werden kann.  Weitere Informationen finden Sie in den Hinweisen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  Gibt `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` zurück, wenn keine erweiterten gibt Informationen abzurufen.  
  
## Hinweise  
 Diese Methode ist mit dem Ziel das Abrufen von Informationen, die nicht auf leiht abgerufen werden, indem die [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)\-Methode aufrufen.  
  
 Im folgenden GUID ist in der Regel so erkannt \(die GUID\-Werte für C\# angegeben werden, da der Name nicht in einer Assembly verfügbar ist\).  Zusätzliches GUID kann zur internen Verwendung erstellt werden.  
  
|Name|GUID|Beschreibung|  
|----------|----------|------------------|  
|guidDocument|{3f98de84\-fee9\-11d0\-b47f\-00a0244a1dd2}|Gibt eine `IUnknown`\-Schnittstelle zum Dokument zurück.  In der Regel kann die [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) von dieser Schnittstelle `IUnknown`\-Schnittstelle ermittelt werden.|  
|guidCodeContext|{e2fc65e\-56ce\-11d1\-b528\-00aax004a8797}|Gibt eine `IUnknown`\-Schnittstelle für den Dokumentenkontext zurück.  In der Regel kann die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) von dieser Schnittstelle `IUnknown`\-Schnittstelle ermittelt werden.|  
|guidCustomViewerSupported|{d9c9da31\-ffbe\-4eeb\-9186\-23121e3c088c}|Gibt eine Zeichenfolge zurück, die die CLSID eines benutzerdefinierten Viewers enthält, in der Regel von einer Ausdrucksauswertung implementiert.|  
|guidExtendedInfoSlot|{6df235ad\-82c6\-4292\-9c97\-7389770bc42f}|Gibt eine 32\-Bit\-Zahl zurück, die die gewünschte Slotnummer darstellt, wenn diese Eigenschaft über eine lokale Adresse des verwalteten Codes darstellt.|  
|guidExtendedInfoSignature|{b5fb6d46\-f805\-417f\-96a3\-8ba737073ffd}|Gibt eine Zeichenfolge zurück, die die Signatur der Variablen enthält, die mit dem Eigenschaftenobjekt zugeordnet ist.|  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)