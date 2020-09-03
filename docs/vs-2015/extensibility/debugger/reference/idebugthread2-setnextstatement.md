---
title: 'IDebugThread2:: SetNextStatement | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 755044ec1d713075c1c1fd3165254ba192943288
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152964"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Legt den aktuellen Anweisungs Zeiger auf den angegebenen Code Kontext fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 Für zukünftige Verwendung reserviert. Legen Sie auf einen NULL-Wert fest.  
  
 `pCodeContext`  
 in Ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) -Objekt, das den Code Speicherort beschreibt, der ausgeführt werden soll, und seinen Kontext.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. In der folgenden Tabelle werden andere mögliche Werte angezeigt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Die nächste Anweisung darf sich nicht in einem Stapel Rahmen befinden, der tiefer auf dem Frame Stapel liegt.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Die Next-Anweisung ist keinem Frame im Stapel zugeordnet.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Einige Debug-engines können die nächste Anweisung nach einer Ausnahme nicht festlegen.|  
  
## <a name="remarks"></a>Bemerkungen  
 Der Anweisungs Zeiger gibt die nächste auszuführende Anweisung oder Anweisung an. Diese Methode wird verwendet, um eine Zeile des Quellcodes zu wiederholen oder um die Fortsetzung der Ausführung in einer anderen Funktion zu erzwingen (z. b.).  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
