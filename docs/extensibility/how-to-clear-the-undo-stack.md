---
title: 'Vorgehensweise: Deaktivieren der Rückgängig-Stapel | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2519d529da13366c706e940b78f57a6ad903de7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-clear-the-undo-stack"></a>Vorgehensweise: Deaktivieren der Rückgängig-Stapel
Die folgende Prozedur unter wird erläutert, wie die Rückgängig-Stapel gelöscht.  
  
### <a name="to-clear-the-undo-stack"></a>So löschen Sie die Rückgängig-Stapel  
  
1.  So löschen Sie die Verwendung der Rückgängig-Stapel der [IOleUndoManager::DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) Methode. Im folgenden finden ein Beispiel dafür:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Implementieren von Rückgängig-Management](../extensibility/how-to-implement-undo-management.md)