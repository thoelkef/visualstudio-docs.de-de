---
title: "Gewusst wie: deaktivieren den R&#252;ckg&#228;ngig-Stapel | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "legacy - Editoren [Visual Studio SDK], deaktivieren Sie Rückgängig-Stapel"
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: deaktivieren den R&#252;ckg&#228;ngig-Stapel
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die folgende der folgenden Prozedur wird erklärt, wie Sie den Rückgängig\-Stapel gelöscht werden.  
  
### Der Rückgängig\-Stapel löschen  
  
1.  Die Verwendung der Rückgängigstapel löschen [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799)\-Methode.  Nachfolgend ist ein Beispiel dafür:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## Siehe auch  
 [Gewusst wie: Implementieren von Rückgängig\-Management](../extensibility/how-to-implement-undo-management.md)