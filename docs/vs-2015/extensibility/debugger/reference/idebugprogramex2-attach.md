---
title: 'IDebugProgramEx2:: Attach | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4fe729f2fc196380a3db1a60d1c32f62bbd70998
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841157"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Fügen Sie eine Sitzung an ein Programm an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pCallback`  
 in Ein [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) -Objekt, das die Rückruffunktion darstellt, an die die angefügte Debug-Engine Ereignisse sendet.  
  
 `dwReason`  
 in Ein Wert aus der [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) Enumeration, die den Grund für den Anfüge Vorgang beschreibt.  
  
 `pSession`  
 in Ein Wert, der die Sitzung eindeutig identifiziert, die an das Programm angefügt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird ein Fehlercode zurückgegeben. Diese Methode sollte zurückgeben, `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` Wenn das Programm bereits angefügt ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Port, der das Programm enthält, kann den Wert in verwenden `pSession` , um zu bestimmen, welche Sitzung versucht, dem Programm anzufügen. Wenn ein Port beispielsweise zulässt, dass jeweils nur eine Debugsitzung an einen Prozess angefügt wird, kann der Port ermitteln, ob dieselbe Sitzung bereits an andere Programme im Prozess angefügt ist.  
  
> [!NOTE]
> Die übergebene Schnittstelle `pSession` muss nur als Cookie behandelt werden. dabei handelt es sich um einen Wert, der den sitzungsdebug-Manager eindeutig identifiziert, der an dieses Programm angefügt wird. keine der Methoden der angegebenen Schnittstelle ist funktionsfähig.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
