---
title: IDebugCustomViewer::DisplayValue | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bda4c60e9164ae195c0e3ba49893b1a818c66f14
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "59001050"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode wird aufgerufen, um den angegebenen Wert anzuzeigen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `hwnd`  
 [in] Übergeordnetes Fenster  
  
 `dwID`  
 [in] ID für den benutzerdefinierten Viewer, die mehr als einen Typ zu unterstützen.  
  
 `pHostServices`  
 [in]: Reserviert Legen Sie immer auf Null.  
  
 `pDebugProperty`  
 [in] Schnittstelle, die verwendet werden kann, zum Abrufen des Werts, der angezeigt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls den Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die Anzeige ist "modal", insofern diese Methode die erforderlichen Fenster erstellt, den Wert zeigt, auf Eingabe warten, und schließen Sie das Fenster, alle vor der Rückgabe an den Aufrufer. Dies bedeutet, dass alle Aspekte, die zum Anzeigen von den Wert der Eigenschaft, von der Erstellung eines Fensters für die Ausgabe für das Warten auf Benutzereingaben, um das Löschen des Fensters von die Methode behandelt werden muss.  
  
 Zur Unterstützung der Änderung des Werts auf die angegebenen [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Objekts verwenden Sie die [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) Methode – Wenn der Wert als Zeichenfolge ausgedrückt werden kann. Andernfalls ist es erforderlich, eine benutzerdefinierte Schnittstelle zu erstellen – ausschließlich für die ausdrucksauswertung Implementierung `DisplayValue` Methode – für das gleiche Objekt, das implementiert die `IDebugProperty3` Schnittstelle. Diese benutzerdefinierte Schnittstelle, die Methoden zum Ändern der Daten von beliebiger Größe oder Komplexität angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
