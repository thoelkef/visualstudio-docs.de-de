---
title: "IDebugCustomViewer::DisplayValue | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer::DisplayValue"
helpviewer_keywords: 
  - "IDebugCustomViewer::DisplayValue"
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode wird aufgerufen, um den angegebenen Wert anzuzeigen.  
  
## Syntax  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```c#  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### Parameter  
 `hwnd`  
 \[in\]  Übergeordnetes Fenster  
  
 `dwID`  
 \[in\]  IDs für benutzerdefinierte Viewer, die mehr als einen Typ unterstützen.  
  
 `pHostServices`  
 \[in\] Reserviert.  Immer auf NULL festgelegt.  
  
 `pDebugProperty`  
 \[in\]  Schnittstelle, die verwendet werden kann, um auf den anzuzeigenden Wert abzurufen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  
  
## Hinweise  
 Die Anzeige ist dadurch, dass diese Methode das notwendige Fenster erstellt, den Wert anzeigt, bei der Eingabe wartet und schließen Sie das Fenster modal all „,“ bevor sie an den Aufrufer zurückkehrt.  Dies bedeutet, dass die Methode alle Aspekte der Anzeige des Werts der Eigenschaft, für das Erstellen eines Fensters für die Ausgabe, um Benutzereingaben zu Antworten Zerstören des Fensters behandelt werden muss.  
  
 Um das Ändern des Werts für das angegebene [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)\-Objekt unterstützt werden sollen, können Sie die [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)\-Methode verwenden, wenn der Wert als Zeichenfolge ausgedrückt werden kann.  Andernfalls ist es erforderlich, eine benutzerdefinierte Schnittstelle zum exklusiven Ausdrucksauswertung zu erstellen, der dieses `DisplayValue` METHOD\-auf demselben Objekt implementiert, das die `IDebugProperty3`\-Schnittstelle implementiert.  Diese benutzerdefinierte Schnittstelle wäre Methoden zum Ändern der Daten eine beliebige Größe oder der Komplexität führen.  
  
## Siehe auch  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)