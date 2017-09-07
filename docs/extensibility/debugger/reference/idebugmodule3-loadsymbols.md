---
title: IDebugModule3::LoadSymbols | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 00b357a7c122de2788875632b770c4346963d975
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Lädt die Symbole für das aktuelle Modul.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Methode erfolgreich ist, gibt es `S_OK`. Falls dies fehlschlägt, wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode lädt die Symbole in den aktuellen Suchpfad (dem kann geändert werden, durch Aufrufen der [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) Methode).  
  
 Diese Methode ist dann vorzuziehen, über die [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
