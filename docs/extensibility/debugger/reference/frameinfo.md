---
title: FRAMEINFO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FRAMEINFO
helpviewer_keywords:
- FRAMEINFO structure
ms.assetid: 95001b89-dddb-45bb-889d-8327994e38a5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5b3fd52fb80cd2bd588951b6a921ca157935a3a2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="frameinfo"></a>FRAMEINFO
Beschreibt einen Stapelrahmen entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct tagFRAMEINFO {   
   FRAMEINFO_FLAGS    m_dwValidFields;  
   BSTR               m_bstrFuncName;  
   BSTR               m_bstrReturnType;  
   BSTR               m_bstrArgs;  
   BSTR               m_bstrLanguage;  
   BSTR               m_bstrModule;  
   UINT64             m_addrMin;  
   UINT64             m_addrMax;  
   IDebugStackFrame2* m_pFrame;  
   IDebugModule2*     m_pModule;  
   BOOL               m_fHasDebugInfo;  
   BOOL               m_fStaleCode;  
   BOOL               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
```csharp  
public struct FRAMEINFO {   
   public uint              m_dwValidFields;  
   public string            m_bstrFuncName;  
   public string            m_bstrReturnType;  
   public string            m_bstrArgs;  
   public string            m_bstrLanguage;  
   public string            m_bstrModule;  
   public ulong             m_addrMin;  
   public ulong             m_addrMax;  
   public IDebugStackFrame2 m_pFrame;  
   public IDebugModule2     m_pModule;  
   public int               m_fHasDebugInfo;  
   public int               m_fStaleCode;  
   public int               m_fAnnotatedFrame;  
} FRAMEINFO;  
```  
  
## <a name="members"></a>Member  
 m_dwValidFields  
 Eine Kombination aus Flags aus der [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) -Enumeration, der angibt, welche Felder ausgefüllt werden.  
  
 m_bstrFuncName  
 Der Funktionsname, die dem Stapelrahmen zugeordnet wird.  
  
 m_bstrReturnType  
 Der Rückgabetyp des Stapelrahmens zugeordnet.  
  
 m_bstrArgs  
 Die Argumente der Funktion, die dem Stapelrahmen zugeordnet.  
  
 m_bstrLanguage  
 Die Sprache, in der die Funktion implementiert wird.  
  
 m_bstrModule  
 Der Modulname der Stapelrahmen zugeordnet.  
  
 m_addrMin  
 Die minimale physischen Stapel-Adresse.  
  
 m_addrMAX  
 Die maximale physischen Stapel-Adresse.  
  
 m_pFrame  
 Die [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Objekt, das diesem Stapelrahmen darstellt.  
  
 m_pFrame  
 Die [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) -Objekt, das das Modul darstellt, das diesem Stapelrahmen enthält.  
  
 m_fHasDebugInfo  
 Ungleich 0 (`TRUE`) wenn Debuginformationen im angegebenen Bereich vorhanden ist.  
  
 m_fHasDebugInfo  
 Ungleich 0 (`TRUE`) Wenn der Stapelrahmen Code zugeordnet ist, die nicht mehr gültig ist.  
  
 m_fHasDebugInfo  
 Ungleich 0 (`TRUE`) Wenn der Stapelrahmen vom Sitzung Debug-Manager (SDM) mit Anmerkungen versehen wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur wird zum Übergeben der [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) Methode ausgefüllt werden. Diese Struktur ist auch in eine Liste der im enthaltene enthalten die [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) -Schnittstelle, die wiederum von einem Aufruf zurückgegeben wird das [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)