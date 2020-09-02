---
title: MessageType | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547207"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt den Nachrichtentyp und den Grund an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Member  
 MT_OUTPUTSTRING  
 Gibt an, dass die Nachricht an das Ausgabefenster gesendet werden soll. Dies schließt sich gegenseitig aus `MT_MESSAGEBOX` .  
  
 MT_MESSAGEBOX  
 Gibt an, dass die Meldung in einem Meldungs Feld angezeigt werden soll. Dies schließt sich gegenseitig aus `MT_OUTPUTSTRING` .  
  
 MT_TYPE_MASK  
 Ein Maskenwert, um das Ziel für die Nachricht zu isolieren.  
  
 MT_REASON_EXCEPTION  
 Gibt an, dass ein Meldungs Feld als Ergebnis einer Ausnahme angezeigt wird. Dies schließt sich gegenseitig aus `MT_REASON_TRACEPOINT` .  
  
 MT_REASON_TRACEPOINT  
 Gibt an, dass ein Meldungs Feld durch das Erreichen eines Ablauf Verfolgungs Punkts angezeigt wird. Dies schließt sich gegenseitig aus `MT_REASON_EXCEPTION` .  
  
 MT_REASON_MASK  
 Ein Maskenwert, um den Grund für die angezeigte Meldung zu isolieren.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Werte werden von der [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) -Methode und der [getErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) -Methode zurückgegeben.  
  
 Einer der Grundwerte kann mit einem der Ausgabeziel Werte mithilfe eines bitweisen kombiniert werden `OR` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
