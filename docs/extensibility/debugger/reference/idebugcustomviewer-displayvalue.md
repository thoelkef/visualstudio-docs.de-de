---
title: IDebugCustomViewer::DisplayValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer::DisplayValue
helpviewer_keywords: IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 74990eac497b8ed239894121eb954cd8eeca55e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Diese Methode wird aufgerufen, um den angegebenen Wert anzuzeigen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [in] ID für den benutzerdefinierten Viewer, die mehrere Typen zu unterstützen.  
  
 `pHostServices`  
 [in] Reserviert. Legen Sie immer auf Null.  
  
 `pDebugProperty`  
 [in] Schnittstelle, die verwendet werden kann, zum Abrufen des Werts angezeigt werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Anzeige ist "gebunden", da diese Methode wird Erstellen des erforderlichen Zeitfensters, zeigt den Wert für die Eingabe zu warten und schließen Sie das Fenster, alle vor der Rückgabe an den Aufrufer. Dies bedeutet, dass die Methode zum Anzeigen von den Wert der Eigenschaft, von der Erstellung eines Fensters für die Ausgabe, um Benutzereingaben zu zerstören das Fenster warten alle Aspekte behandelt werden muss.  
  
 Zur Unterstützung der Änderung des Werts auf die angegebenen [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Objekt können Sie die [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) Methode – Wenn der Wert als Zeichenfolge ausgedrückt werden kann. Andernfalls ist es notwendig, eine benutzerdefinierte Benutzeroberfläche erstellen – exklusiv für die ausdrucksauswertung zur Implementierung `DisplayValue` Methode – für das gleiche Objekt, das implementiert die `IDebugProperty3` Schnittstelle. Diese benutzerdefinierte Schnittstelle, die Methoden zum Ändern der Daten ein beliebiger Größe und Komplexität angeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)