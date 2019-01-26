---
title: 'Vorgehensweise: Deaktivieren den Rückgängig-Stapel | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71c8e80fceef685b49af53fb5c369500315bbea9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000167"
---
# <a name="how-to-clear-the-undo-stack"></a>Vorgehensweise: Deaktivieren des Rückgängig-Stapels
Das folgende Verfahren unten wird erläutert, wie den Rückgängigstapel.  
  
## <a name="to-clear-the-undo-stack"></a>Auf den Rückgängigstapel.  
  
1.  Löschen Sie die Verwendung der Rückgängig-Stapel der [IOleUndoManager::DiscardFrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) Methode. Im folgenden finden ein Beispiel hierfür:  
  
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
 [Vorgehensweise: Implementieren von Rückgängig-Verwaltung](../extensibility/how-to-implement-undo-management.md)