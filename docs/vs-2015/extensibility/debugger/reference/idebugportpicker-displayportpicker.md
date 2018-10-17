---
title: IDebugPortPicker::DisplayPortPicker | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e718df47b45c66b32d88b57b69d81b8f69b9077c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285804"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zeigt das angegebene Dialogfeld an, das dem Benutzer ermöglicht, einen Port auszuwählen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `hwndParentDialog`  
 [in] Handle für das übergeordnete Dialogfeld.  
  
 `pbstrPortId`  
 [out] Port-ID-Zeichenfolge.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Der Rückgabewert `S_FALSE` (oder einen Rückgabewert von `S_OK` mit der `BSTR` festgelegt `NULL`) gibt an, dass der Benutzer geklickt hat **Abbrechen**.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)

