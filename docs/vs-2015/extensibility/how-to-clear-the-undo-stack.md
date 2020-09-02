---
title: 'Gewusst wie: Löschen des Rückgängig-Stapels | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: db77f93fd7f6af16b5358b75b6ffcd5927430653
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62549168"
---
# <a name="how-to-clear-the-undo-stack"></a>Vorgehensweise: Leeren des Stapels zum Rückgängigmachen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im folgenden Verfahren wird erläutert, wie der Rückgängig-Stapel gelöscht wird.  
  
### <a name="to-clear-the-undo-stack"></a>So löschen Sie den Rückgängig-Stapel  
  
1. Verwenden Sie die Methode [IOleUndoManager::D iscardfrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) , um den Rückgängig-Stapel zu löschen. Im folgenden finden Sie ein Beispiel hierfür:  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Implementieren der Rückgängig-Funktion](../extensibility/how-to-implement-undo-management.md)
