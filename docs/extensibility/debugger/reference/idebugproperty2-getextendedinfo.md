---
title: IDebugProperty2::GetExtendedInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetExtendedInfo
helpviewer_keywords: IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7456ebe1e28618270bd90f09186ec49814c62b66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Ruft Informationen für die Eigenschaft erweitert werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `guidExtendedInfo`  
 [in] GUID, der bestimmt, welche erweiterten Informationen abgerufen werden sollen. Einzelheiten finden Sie unter "Hinweise".  
  
 `pExtendedInfo`  
 [out] Gibt eine `VARIANT` (C++) oder ein Objekt (c#), die zum Abrufen von Informationen über die erweiterte Eigenschaft verwendet werden kann. Dieser Parameter möglicherweise zurück, z. B. ein `IUnknown` -Schnittstelle, die abgefragt werden kann eine [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) Schnittstelle. Einzelheiten finden Sie unter "Hinweise".  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird Fehlercode zurückgegeben. Gibt `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` Wenn es keine erweiterten Informationen sind abgerufen.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode zum Abrufen von Informationen, die nicht selbst geeignet ist, wird durch den Aufruf abgerufen vorhanden ist die [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Methode.  
  
 Die folgenden GUIDs werden in der Regel von dieser Methode erkannt (die GUID-Werte werden für c# angegeben, da der Name nicht in jeder beliebigen Assembly verfügbar ist). Zusätzliche GUIDs können für die interne Verwendung erstellt werden.  
  
|Name|GUID|Beschreibung|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Gibt eine `IUnknown` Schnittstelle, um das Dokument. In der Regel die [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) Schnittstelle abgerufen werden kann, aus dieser `IUnknown` Schnittstelle.|  
|guidCodeContext|{e2fc65e 56ce - 11d 1-b528-00aax004a8797}|Gibt eine `IUnknown` Schnittstelle, um den Dokumentenkontext. In der Regel die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Schnittstelle abgerufen werden kann, aus dieser `IUnknown` Schnittstelle.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Gibt eine Zeichenfolge mit der CLSID von einem benutzerdefinierten Viewer, die in der Regel von der ausdrucksauswertung implementiert.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Gibt eine 32-Bit-Zahl, die die gewünschten Slotnummer darstellt, wenn diese Eigenschaft stellt eine lokale Adresse für verwalteten Code dar.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Gibt eine Zeichenfolge, die die Signatur der Property-Objekt zugeordneten Variablen enthält.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)